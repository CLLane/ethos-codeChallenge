<template>
  <div id="app">
    <nav>
      <button v-if="route !== 'create'" v-on:click="route = 'create'">Create Recipe</button>
      <CreateRecipe v-if="route === 'create'" @create-card="createRecipeCard"></CreateRecipe>
      <button v-on:click="route = 'search'">Search Recipes</button>
      <button v-on:click="route = 'browse'">Browse Recipes</button>
    </nav>
  </div>
</template>

<script>
import CreateRecipe from './components/CreateRecipe.vue'

export default {
  name: 'App',
  data () {
    return {
      route: '',
      cards: []
    }
  },
  methods: {
    createRecipeCard(e, title, ingredients, instructions, rating ) {
      const card = {title, ingredients, instructions, rating}
      this.cards.push(card)
    }
  },
  components: {
    CreateRecipe
  }
}
</script>

<style>
  #app {
    display: flex;
  }
  nav {
    display: flex;
    flex-direction: column;
    width: 33%;
  }
</style>
