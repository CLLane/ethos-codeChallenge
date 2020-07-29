<template>
<article>
  <h1>{{card.title}}</h1>
  <p>{{card.ingredients}}</p>
  <p>{{card.instructions}}</p>
  <p>{{card.rating}}</p>
  <button v-on:click="clearCard">x</button>
</article>
</template>
<script>
export default {
  name: 'RecipeCard',
  props: ["card"],
  methods: {
    clearCard(){
      
      this.$emit("clear-card")
    }
  }
}
</script>
<style scoped>

</style>