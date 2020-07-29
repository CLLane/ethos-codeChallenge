<template>
  <form>
    <label for="title">Title</label>
    <input id="title" v-model="title" placeholder="Title of recipe..."/>
    <lable for="ingredients">Ingredients</lable>
    <textarea id="ingredients" v-model="ingredients" placeholder="List of ingredients..."></textarea>
    <label for="instructions">Instructions:</label>
    <textarea id="instructions" v-model="instructions" placeholder="Detailed instructions... "></textarea>
    <label for="rating">Rating:</label>
    <select id="rating" v-model.number="rating">
      <option>1</option>
      <option>2</option>
      <option>3</option>
      <option>4</option>
      <option>5</option>
    </select>
    <button v-if="title && instructions && ingredients && rating">Create Recipe Card</button>
    <button>Clear</button>
  </form>
</template>

<script>
export default {
  name: "CreateRecipe",
  data() {
    return {
      title: "",
      instructions: "",
      ingredients: "",
      rating: "",
    };
  },
  components: {}
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
form {
  display: flex;
  flex-direction: column;
}
</style>
