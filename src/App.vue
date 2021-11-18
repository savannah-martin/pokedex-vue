<template>
  <nav>NAVIGATION</nav>
  <partyPokemon :partyPokemon="pp" @remove-pokemon="remove" />
  <footer><p>&copy; 2021</p></footer>
</template>

<script>
import PartyPokemon from "./components/PartyPokemon.vue";

export default {
  name: "App",
  components: {
    PartyPokemon,
  },
  data() {
    return {
      pp: [
        { name: "Charmander", id: 3 },
        { name: "Bulbasaur", id: 2 },
        { name: "Pikachu", id: 4 },
      ],
    };
  },
  methods: {
    remove(id) {
      this.pp.filter(p => p.id != id);
    },
    async loadPokemon() {
      // load all pokemon from API
      // const pokemon_count = 150;
      // let pokemon = [];
      // for (let i = 1; i <= pokemon_count; i++) {
      //   let p = await getPokemon(i);
      //   if (p.name === "mr-mime") {
      //     p.name = "Mr. Mime";
      //   }
      //   p.isFavorite = false;
      //   pokemon.push(p);
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
