<template>
  <div>
    <h2>Search for Gifs</h2>
    <input type="text" placeholder="Filter Search" v-model="query" />
    <div>
      {{ query }}
    </div>
    <br /><br />
    <button @click="reset">Reset</button>
    <SearchResults :query="query" />
  </div>
</template>

<script>
import { ref } from "vue";
import SearchResults from "./SearchResults.vue";

export default {
  components: {
    SearchResults,
  },
  setup() {
    const query = ref("");
    const reset = () => {
      query.value = "";
    };
    return {
      query,
      reset,
    };
  },
};
</script>

<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
