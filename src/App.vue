<template>
  <div id="app">
    <nav>
      <button v-if="route !== 'create'" v-on:click="route = 'create'">Create Recipe</button>
      <button v-on:click="route = 'search'" v-if="route !== 'search'">Search Recipes</button>
      <button v-on:click="route = 'browse'" v-if="route !== 'browse'">Browse Recipes</button>
    </nav>
    <CreateRecipe v-if="route === 'create'" @create-card="createRecipeCard"></CreateRecipe>
    <BrowseRecipes v-bind:cards="cards" v-if="route === 'browse'"></BrowseRecipes>
    <SearchRecipes v-bind:results="filteredCards" v-if="route === 'search'" @query-cards="searchRecipeCards" 
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
    clearQuery(){
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
#app {
  display: flex;
}
nav {
  display: flex;
  flex-direction: column;
  width: 33%;
}
div {
  width: 100%;
}
</style>
