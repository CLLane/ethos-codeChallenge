<template>
  <div v-if="query === true">
    <p v-if="results.length < 1">No recipes match your query please make try again</p>
    <div v-for="result in results" v-bind:key="result">
      <article>
        <h1>{{result.title}}</h1>
        <p>{{result.ingredients}}</p>
        <p>{{result.instructions}}</p>
        <p>{{result.rating}}</p>
      </article>
    </div>
     <button v-on:click="clearInputs">Search Again</button>
  </div>
  <div v-else>
    <select id="key" v-model="key">
      <option>Title</option>
      <option>Ingredients</option>
      <option>Instructions</option>
      <option>Rating</option>
    </select>
    <input v-model="queryInput">
    <button v-on:click="queryCards">Search</button>
  </div>
</template>
<script>
export default {
  name: "SearchRecipes",
  data() {
    return {
      query: false,
      key: "",
      queryInput: ''
    };
  },
  props: ["results"],
  methods: {
    queryCards(e) {
      e.preventDefault();
      this.$emit('clear-query')
      this.$emit('query-cards', this.key, this.queryInput)
      this.query = !this.query
    },
    clearInputs(e) {
      e.preventDefault();
      this.key = '';
      this.queryInput = '';
      this.query = !this.query;
    }
  },
  components: {
    // RecipeCard
  }
};
</script>
<style scoped>
article {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>