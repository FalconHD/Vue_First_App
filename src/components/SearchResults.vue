<template>
  <div>
    <div v-if="fetchedData">
      <span v-for="item in fetchedData" :key="item.id">
        <img :src="item.images.downsized.url" alt="" />
      </span>
    </div>
    <div v-else>
      <h1>loading</h1>
    </div>
  </div>
</template>

<script>
import { ref, watchEffect } from "vue";
export default {
  props: {
    query: String,
  },
  setup(props) {
    const fetchedData = ref([]);
    watchEffect(() => {
      fetch(
        `https://api.giphy.com/v1/gifs/search?api_key=${process.env.VUE_APP_SECRET_KEY}&q=${props.query}`
      )
        .then((response) => response.json())
        .then(({ data }) => {
          fetchedData.value = data;
        });
    });

    return {
      fetchedData,
    };
  },
};
</script>

<style lang="css">
img {
  min-width: 300px;
  max-width: 300px;
  min-height: 300px;
  max-height: 300px;
}
</style>
