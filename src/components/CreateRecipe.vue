<template>
  <form>
    <label for="title">Title</label>
    <input id="title" v-model="title" placeholder="Title of recipe..." />
    <label for="ingredients">Ingredients</label>
    <textarea id="ingredients" v-model="ingredients" placeholder="List of ingredients..."></textarea>
    <label for="instructions">Instructions:</label>
    <textarea id="instructions" v-model="instructions" placeholder="Detailed instructions... "></textarea>
    <label for="rating">Rating:</label>
    <select id="rating" v-model.number="rating">
      <option>0</option>
      <option>1</option>
      <option>2</option>
      <option>3</option>
      <option>4</option>
      <option>5</option>
    </select>
    <button
      v-if="title && instructions && ingredients && rating"
      v-on:click="createCard"
    >Create Recipe Card</button>
    <button v-on:click="clearInputs">Clear</button>
  </form>
</template>

<script>
export default {
  name: "CreateRecipe",
  data() {
    return {
      title: "",
      ingredients: "",
      instructions: "",
      rating: ""
    };
  },
  methods: {
    createCard(e) {
      e.preventDefault();
      this.$emit(
        "create-card",
        e,
        this.title,
        this.ingredients,
        this.instructions,
        this.rating
      );
      this.clearInputs();
    },
    clearInputs(e) {
      e.preventDefault();
      this.title = "";
      this.ingredients = "";
      this.instructions = "";
      this.rating = "";
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
form {
  display: flex;
  flex-direction: column;
}
</style>
