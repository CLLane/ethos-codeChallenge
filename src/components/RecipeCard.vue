<template>
  <article>
    <h1>{{card.title}}</h1>
    <h5>Ingredients</h5>
    <p>{{card.ingredients}}</p>
    <h5>Instructions</h5>
    <p>{{card.instructions}}</p>
    <h5>Rating</h5>
    <p>{{card.rating}}</p>
    <button v-on:click="clearCard">x</button>
  </article>
</template>
<script>
export default {
  name: "RecipeCard",
  props: ["card"],
  methods: {
    clearCard() {
      this.$emit("clear-card");
    }
  }
};
</script>
<style scoped>
  article {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 18vw;
    border: 2px solid lightgray;
    border-radius: 8px;
    margin: 2vh;
  }
  button {
    align-self: flex-end;
    width: 2vw;
  }
  button:hover{
    cursor: pointer;
  }
</style>