<template>
  <div id="party">
    <h2 class="px-3">Party</h2>
    <h3 class="mx-4">{{ partyPokemon.length }} of 6</h3>
  </div>
  <div class="party-pokemon">
    <!-- pokemon cards go here -->
    <PokemonCard
      v-for="p in partyPokemon"
      :key="p.id"
      :pokemon="p"
      :clickAction="removePokemon"
      @click-pokemon="remove"
    />
  </div>
</template>

<script>
import PokemonCard from "./PokemonCard.vue";

export default {
  name: "PartyPokemon",
  components: { PokemonCard },
  props: {
    partyPokemon: Array,
  },
  methods: {
    remove(guid) {
      this.$emit("remove-pokemon", guid);
    },
  },
};
</script>

<style>
#party {
  margin-top: 85px;
  background-color: #fff;
  width: 100%;
  /* min-height: 350px; */
  /* height: auto; */
  display: flex;
  flex-direction: column;
  justify-content: start;
  flex-wrap: wrap;
  text-align: left;
}

.party-pokemon {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
</style>
