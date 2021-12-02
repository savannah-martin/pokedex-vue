<template>
  <div id="allPokemon">
    <h2>All Pokemon</h2>
  </div>
  <div class="all-pokemon">
    <!-- pokemon cards go here -->
    <PokemonCard
      v-for="p in allPokemon"
      :key="p.id"
      :pokemon="p"
      :clickAction="addPokemon"
      @remove-pokemon="add"
    />
  </div>
</template>

<script>
import PokemonCard from "./PokemonCard.vue";

export default {
  name: "AllPokemon",
  components: { PokemonCard },
  props: {
    allPokemon: Array,
  },
};
</script>

<style>
#allPokemon {
  /* overflow: scroll; */
  height: 60vh;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
</style>
