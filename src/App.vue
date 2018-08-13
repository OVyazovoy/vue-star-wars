<template>
  <div v-if="loaded" id="app">
    <div  class="title">
      <h1>
        {{ episod_name }}
        <span>{{ episode_id }}</span>
      </h1>
      <span class="release_date">{{ date }}</span>
    </div>      
    <div id="moveInfo">
      <p class="director">director</p>
      <p class="producer">producer</p>
    </div>

    <CharactersList v-bind:characters="charactersList"/>

  </div>

  <div v-else id="app">
    loading
  </div>
</template>

<script>
import moment from "moment";
import CharactersList from "./components/CharactersList";

export default {
  mounted() {
    this.fetchData();
  },
  name: "app",
  data() {
    return {
      episod_name: "---",
      episode_id: 1,
      date: "----",
      charactersList: [],
      loaded: false
    };
  },
  methods: {
    changeEpisodeName(event) {
      this.episod_name = event.target.value;
    },
    add() {
      this.episode_id += 1;
    },
    fetchData() {
      fetch("https://swapi.co/api/films/1")
        .then(response => response.json())
        .then(response => {
          this.episod_name = response.title;
          this.episode_id = response.episode_id;
          this.loaded = true;
          this.date = moment(response.created).format("YYYY mm dd ");
          this.charactersList = response.characters;
        });
    }
  },
  components: {
    CharactersList
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: grid;
  grid-template-columns: 1fr 1fr;
  width: 50%;
  max-width: 50%;
  margin: 0 auto;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background-color: antiquewhite;
}
.title {
  grid-column-start: 1;
  grid-column-end: 3;
}

#charactersList {
  background-color: aquamarine;
}
</style>
