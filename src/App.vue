<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark fixed-top">
    <div class="container-fluid">
      <a class="navbar-brand" href="#">Pokedex</a>
      <form class="form-inline" @submit.prevent="filterPokemon(inputValue)">
        <input
          v-model="inputValue"
          class="mr-sm-2 p-1 m-2"
          placeholder="Search"
          aria-label="Search"
        />
        <button
          class="btn btn-outline-light my-2 my-sm-0 mx-1"
          @click="filterPokemon(inputValue)"
        >
          Search
        </button>
        <button
          type="button"
          class="btn btn-outline-light my-2 my-sm-0 mx-1"
          @click="clearPokemon"
        >
          Clear
        </button>
        <button
          type="button"
          class="btn btn-outline-light my-2 my-sm-0"
          @click="loadPokemon()"
        >
          Load
        </button>
      </form>
    </div>
  </nav>
  <PartyPokemon :partyPokemon="partyPokemon"/>
  <AllPokemon :allPokemon="allPokemon"/>
  <footer class="fixed-bottom">
    <p>&copy; 2021</p>
  </footer>
</template>

<script>
import PartyPokemon from "./components/PartyPokemon.vue";
import AllPokemon from "./components/AllPokemon.vue";
const getPokemon = async function (id) {
  // get pokemon data from pokeapi
  const url = `https://pokeapi.co/api/v2/pokemon/${id}`;

  const response = await fetch(url);
  const data = await response.json();

  return data;
  //createPokemonCard( data );
};

export default {
  name: "App",
  getPokemon: async function (id) {
    // get pokemon data from pokeapi
    const url = `https://pokeapi.co/api/v2/pokemon/${id}`;

    const response = await fetch(url);
    const data = await response.json();

    return data;
    //createPokemonCard( data );
  },
  components: {
    PartyPokemon,
    AllPokemon,
  },
  data() {
    return {
      allPokemon: [],
      partyPokemon: [],
      filteredPokemon: [],
      maxPartySize: 6,
      inputValue: "",
    };
  },
  methods: {
    remove(id) {
      this.allPokemon.filter((p) => p.id != id);
    },
    async loadPokemon() {
      // load all pokemon from API and save into all pokemon
      const pokemon_count = 150;
      let pokemon = [];
      for (let i = 1; i <= pokemon_count; i++) {
        let p = await getPokemon(i);
        if (p.name === "mr-mime") {
          p.name = "Mr. Mime";
        }
        p.isFavorite = false;

        pokemon.push(p);
      }

      pokemon.forEach((p) => {
        this.allPokemon.push(p);
      });
    },
  },
};
</script>

<style>
@import "https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
