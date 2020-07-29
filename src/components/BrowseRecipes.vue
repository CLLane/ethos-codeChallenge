<template>
  <div>
    <p v-if="cards.length < 1">You have no recipes to browse please create one</p>
    <div v-for="card in cards" v-bind:key="card">
      <article>
        <h1>{{card.title}}</h1>
        <p>{{card.ingredients}}</p>
        <p>{{card.instructions}}</p>
        <p>{{card.rating}}</p>
      </article>
    </div>
  </div>
</template>
<script>
export default {
  name: "BrowseRecipes",
  props: ['cards'],
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