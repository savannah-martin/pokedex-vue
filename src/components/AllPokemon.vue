<template>
  <div id="allPokemon">
    <h2>All Pokemon</h2>
  </div>
  <div id="all-pokemon">
      <PokemonCard
        v-for="p in allPokemon"
        :key="p.id"
        :pokemon="p"
        :clickAction="addPokemon"
        @add-pokemon="add"
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
  methods: {
   add(id) {
     this.emit("add-pokemon", id);
   },
  },
};
</script>

<style>
#allPokemon {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

#all-pokemon {
  /* overflow: scroll; */
  height: 60vh;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
</style>
