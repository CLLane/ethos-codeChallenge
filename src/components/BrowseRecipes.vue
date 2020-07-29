<template>
  <div v-if="showCard === false">
    <p v-if="cards.length < 1">You have no recipes to browse please create one</p>
    <div v-for="(card,i) in cards" v-bind:key="card">
      <h1 v-on:click="toggleShowCard(i)">{{card.title}}</h1>
    </div>
  </div>
  <div v-else>
    <RecipeCard @clear-card="toggleShowCard" v-bind:card="cards[cardIndex]"></RecipeCard>
  </div>
</template>

<script>
import RecipeCard from "./RecipeCard.vue";

export default {
  name: "BrowseRecipes",
  data() {
    return {
      showCard: false,
      cardIndex: null
    };
  },
  methods: {
    toggleShowCard(i) {
      this.showCard = !this.showCard;
      this.cardIndex = i;
    }
  },
  props: ["cards"],
  components: {
    RecipeCard
  }
};
</script>

<style scoped>
  div {
    display: flex;
    flex-direction: column;
    align-items: center;
    width: 100vw;
  }
  article {
    display: flex;
    flex-direction: column;
    align-items: center;
  }
  h1:hover {
    cursor: pointer;
  }
</style>