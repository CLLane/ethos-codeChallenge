<template>
  <div id="app">
    <nav>
      <button v-if="route !== 'create'" v-on:click="route = 'create'">Create Recipe</button>
      <button v-else disabled>Create Recipe</button>
      <button v-if="route !== 'search'" v-on:click="route = 'search'">Search Recipes</button>
      <button v-else disabled>Search Recipe</button>
      <button v-if="route !== 'browse'" v-on:click="route = 'browse'">Browse Recipes</button>
      <button v-else disabled>Browse Recipe</button>
    </nav>
    <CreateRecipe v-if="route === 'create'" @create-card="createRecipeCard"></CreateRecipe>
    <BrowseRecipes v-if="route === 'browse'" v-bind:cards="cards"></BrowseRecipes>
    <SearchRecipes
      v-bind:results="filteredCards"
      v-if="route === 'search'"
      @query-cards="searchRecipeCards"
      @clear-query="clearQuery"
    ></SearchRecipes>
  </div>
</template>

<script>
import CreateRecipe from "./components/CreateRecipe.vue";
import BrowseRecipes from "./components/BrowseRecipes.vue";
import SearchRecipes from "./components/SearchRecipes.vue";

export default {
  name: "App",
  data() {
    return {
      route: "",
      cards: [],
      filteredCards: []
    };
  },
  methods: {
    createRecipeCard(title, ingredients, instructions, rating) {
      const card = { title, ingredients, instructions, rating };
      this.cards.push(card);
    },
    searchRecipeCards(key, input) {
      let lowerKey = key.toLowerCase();
      this.cards.forEach(card => {
        if (card[lowerKey].includes(input) || card.lowerKey === input) {
          this.filteredCards.push(card);
        }
      });
    },
    clearQuery() {
      this.filteredCards = [];
    }
  },
  components: {
    CreateRecipe,
    BrowseRecipes,
    SearchRecipes
  }
};
</script>

<style scope>
nav {
  display: flex;
  justify-content: space-around;
  align-items: center;
  width: 100vw;
  height: 10vh;
  background: lightskyblue;
}
button {
  border: none;
  border-radius: 8px;
  height: 5vh;
  width: 10vw;
}
body {
  margin: 0px;
}
</style>
