<template>
  <div v-if="filteredPokemon.length > 0" id="filter">
    <h2>Filtered Pokemon</h2>
    <div id="filtered-pokemon">
      <PokemonCard
        v-for="p in filteredPokemon"
        :key="p.id"
        :pokemon="p"
        :clickAction="addPokemon"
        @click-pokemon="add"
      />
    </div>
  </div>
</template>

<script>
import PokemonCard from "./PokemonCard.vue";

export default {
  name: "FilteredPokemon",
  components: { PokemonCard },
  props: {
    filteredPokemon: Array,
  },
  methods: {
    add(guid) {
      this.$emit("add-pokemon", guid);
    },
  },
};
</script>

<style>
#filtered-pokemon {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
</style>
