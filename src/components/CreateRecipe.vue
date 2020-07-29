<template>
<div class="form-container">
  <form>
    <label for="title">Title</label>
    <input id="title" v-model="title" placeholder="Title of recipe..." />
    <label for="ingredients">Ingredients</label>
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
    <div class="button-container">
      <button
        v-if="title && instructions && ingredients && rating"
        v-on:click="createCard"
      >Create Recipe Card</button>
      <button v-else disabled>Create Recipe Card</button>
      <button v-if="title || instructions || ingredients || rating" v-on:click="clearInputs">Clear</button>
      <button v-else disabled>Clear</button>
    </div>
  </form>
  </div>
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
        this.title,
        this.ingredients,
        this.instructions,
        this.rating
      );
      this.clearInputs(e);
    },
    clearInputs(e) {
      e.preventDefault();
      this.title = "";
      this.ingredients = "";
      this.instructions = "";
      this.rating = "";
    }
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
form {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  height: 50vh;
  width: 50vw;
}
button {
  margin-left: 2.5vw;
  margin-right: 2.5vw;
}
input, textarea, select {
  border-radius: 8px;
  border: 2px solid lightgray;
}
label {
  font-size: 20px;
}
.form-container {
  display: flex;
  justify-content: center;
  width: 100vw;
}
.button-container {
  display: flex;
  justify-content: center;
}
#rating {
  width: 5vw;
}
</style>
