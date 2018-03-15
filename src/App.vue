<template>
  <div id="app">
    <h1>Marvel Heroes</h1>
    <div class="allimages">
      <Character v-for="character in characters"  :key="character.id" :character="character"/>
    </div>
    <div class="pagination">
      <button @click="showPrevious" type="button">Previous</button>
      <button @click="showNext" class="buttonNext" type="button">Next</button>
    </div>
    
    
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
      offset: 100,
      characters: [],
    };
  },

  methods: {
    showNext() {
        this.offset=this.offset+20;
        fetch('https://gateway.marvel.com/v1/public/characters?offset=' + this.offset + '&apikey=82036cba2c097a8111714b4acc5d125a')
        .then(res => res.json())
        .then(json => json.data.results)
        .then(characters => {
          this.characters = characters;
        });
      },

    showPrevious() {
      this.offset=this.offset-20;
      fetch('https://gateway.marvel.com/v1/public/characters?offset=' + this.offset + '&apikey=82036cba2c097a8111714b4acc5d125a')
      .then(res => res.json())
      .then(json => json.data.results)
      .then(characters => {
        this.characters = characters;
      });
    }
  },
  
  created() {
    fetch('https://gateway.marvel.com/v1/public/characters?offset=' + this.offset + '&apikey=82036cba2c097a8111714b4acc5d125a')
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
  background-color: rgb(24, 23, 36);
  color: white;
  margin: 0;
}

.allimages {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}

h1 {
  font-family: 'Rammetto One', cursive;
  font-size: 70px;
  font-style: italic;
  text-shadow: -1px 0 yellow, 0 1px black, 1px 0 black, 0 -1px black;
  text-align: center;
  padding: 30px 0;
  margin: 0;
  border-bottom: 2px solid yellow;
}

.pagination {
  display: flex;
  justify-content: flex-end;
  padding: 30px 50px 30px 0;
  font-size: 20px;
}

button {
  font: inherit;
  border: inherit;
  cursor: pointer;
}



.buttonNext {
  margin-left: 30px; 
}

</style>
