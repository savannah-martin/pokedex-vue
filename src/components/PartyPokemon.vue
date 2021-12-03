<template>
  <div id="party">
    <h2>Party</h2>
    <h3>{{ partyPokemon.length }} of 6</h3>
  </div>
  <div class="party-pokemon">
    <!-- pokemon cards go here -->
    <PokemonCard
        v-for="p in partyPokemon"
        :key="p.id"
        :pokemon="p"
        :clickAction="removePokemon"
        @remove-pokemon="remove"
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
    remove(id) {
      this.emit("remove-pokemon", id);
    },
  },
};
</script>

<style>

#party {
  background-color: #fff;
  /* position: sticky; */
  /* left: 0; */
  margin-top: 70px;
  min-height: 30vh;
  /* max-height: 40vh; */
  width: 100%;
  height: auto;
}

#party-pokemon {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
</style>
