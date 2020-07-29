<template>
  <div class="results-container" v-if="query === true">
    <h1>Results:</h1>
    <p v-if="results.length < 1">No recipes match your query please make try again</p>
    <div v-for="result in results" v-bind:key="result">
      <article>
        <h1>{{result.title}}</h1>
        <h5>Ingredients</h5>
        <p>{{result.ingredients}}</p>
        <h5>Instructions</h5>
        <p>{{result.instructions}}</p>
        <h5>Rating</h5>
        <p>{{result.rating}}</p>
      </article>
    </div>
    <button v-on:click="clearInputs">Search Again</button>
  </div>
  <div class="search-container" v-else>
    <label for="key">Type:</label>
    <select id="key" v-model="key">
      <option>Title</option>
      <option>Ingredients</option>
      <option>Instructions</option>
      <option>Rating</option>
    </select>
    <label for="phrase">Phrase:</label>
    <input v-model="queryInput" id="phrase" />
    <button v-if="key && queryInput" v-on:click="queryCards">Search</button>
    <button v-else disabled>Search</button>
  </div>
</template>
<script>
export default {
  name: "SearchRecipes",
  data() {
    return {
      query: false,
      key: "",
      queryInput: ""
    };
  },
  props: ["results"],
  methods: {
    queryCards(e) {
      e.preventDefault();
      this.$emit("clear-query");
      this.$emit("query-cards", this.key, this.queryInput);
      this.query = !this.query;
    },
    clearInputs(e) {
      e.preventDefault();
      this.key = "";
      this.queryInput = "";
      this.query = !this.query;
    }
  },
  components: {
    // RecipeCard
  }
};
</script>
<style scoped>
.search-container {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100vw;
}
article {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 18vw;
  border: 2px solid lightgray;
  border-radius: 8px;
  margin: 2vh;
}
select,
input {
  margin: 1.5vw;
  border-radius: 8px;
  height: 3vh;
  border: 2px solid lightgray;
}
.results-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  width: 100%;
}
</style>