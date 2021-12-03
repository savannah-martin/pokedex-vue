<template>
  <!-- <div class="pokemon" @click="clickAction">
    <h1>{{ pokemon.name }}</h1>
    <h1>{{ pokemon.id }}</h1> -->

  <div class="pokemon" @click="click">
    <div class="img-container">
      <img :src="pokemon.sprites.other['official-artwork'].front_default" />
    </div>
    <div class="info">
      <span class="number">#{{ pokemon.id }}</span>
      <h3 class="name" style="text-transform: capitalize">
        {{ pokemon.name }}
      </h3>
      <small class="type">
        Type:
        {{ pokemon.type }}
      </small>
    </div>
  </div>

  <!-- </div> -->
</template>

<script>
export default {
  name: "PokemonCard",
  props: {
    pokemon: Object,
    clickAction: String,
  },
  data() {
    return {};
  },
  methods: {
    //actually do GUID
    getGUID() {
      return Math.floor(Math.random() * 1000000);
    },
    click() {
      this.$emit("click-pokemon", this.pokemon.guid);
    },
  },
};
</script>

<style>
.pokemon {
  display: flex;
  flex-direction: column;
  align-items: center;
  flex-basis: 15%;
  background-color: #eee;
  border-radius: 10px;
  box-shadow: 0 3px 15px rgba(100, 100, 100, 0.5);
  margin: 10px;
  padding: 20px;
  text-align: center;
  transform: scale(1);
  transition: all 0.2s;
  cursor: pointer;
  max-height: 275px;
}

.pokemon:hover {
  transform: scale(1.05);
}

.pokemon .img-container {
  background-color: rgba(255, 255, 255, 0.5);
  border-radius: 50%;
  width: 100px;
  height: 100px;
  text-align: center;
}

.pokemon .img-container img {
  max-width: 100px;
  width: 120%;
  margin-top: 00px;
}

.pokemon .info {
  margin-top: 20px;
}

.pokemon .info .number {
  background-color: rgba(0, 0, 0, 0.1);
  padding: 5px 10px;
  border-radius: 10px;
  font-size: 0.8em;
}

.pokemon .info .name {
  font-family: "Playfair Display", serif;
  font-weight: 400;
  margin: 15px 0 7px;
  letter-spacing: 1px;
}

.pokemon .info small {
  font-size: 0.7em;
  text-transform: capitalize;
  font-weight: 200;
}
</style>
