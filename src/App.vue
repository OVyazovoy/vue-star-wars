<template>
  <div id="app">
    <div class="title">
      <h1>
        {{ episod_name }}
        <span>{{episode_id}}</span>
      </h1>
      <span class="release_date">date</span>
    </div>
    <button @click="add">add</button>
    <input v-model="episod_name" type="text">
      
    <div id="moveInfo">
      
      <p class="director">director</p>
      <p class="producer">producer</p>
    </div>
    <ul id="charactersList">
      <li>one</li>
    </ul>
  </div>
</template>

<script>

export default {
  name: 'app',
  data() {
    return {
      episod_name: "Some episode name",
      episode_id: 1
    };
  },
  methods: {
      changeEpisodeName(event){
        this.episod_name = event.target.value;
      },
      add(){
        this.episode_id += 1;
      }
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
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

#charactersList{
  background-color: aquamarine
}
</style>
