<template>
  <div id="app">
    <h1>Marvel Heroes</h1>
    <Character v-for="character in characters"  :key="character.id" :character="character"/>
  </div>
</template>

<script>
import Character from './components/Character'

export default {
  name: 'App',
  components: {
    Character
  },

  data () {
    return {
      characters: []
    };
  },

  created() {
    fetch('https://gateway.marvel.com/v1/public/characters?offset=100&apikey=82036cba2c097a8111714b4acc5d125a')
    .then(res => res.json())
    .then(json => json.data.results)
    .then(characters => {
      this.characters = characters;
    });
  }

}
</script>

<style>

body {
  margin: 0;
}

#app {
  background-color: rgb(61, 172, 144);
  color: white;
  margin: 0;
}

h1 {
  font-family: 'Rammetto One', cursive;
  font-size: 70px;
  font-style: italic;
  text-shadow: -1px 0 black, 0 1px black, 1px 0 black, 0 -1px black;
  text-align: center;
  padding: 30px 0;
  margin: 0;
}

</style>
