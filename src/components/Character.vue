<template>
  <div class="background">
    <div class="containerHeroes">
      <div class="firstDetail">
        <h2>
          {{character.name}}
        </h2>
        <div class="images" :style="{ backgroundImage: 'url(' + character.thumbnail.path + '.' + character.thumbnail.extension + ')' }">
        </div> 
      </div>
      
      <div v-if="showDetail">
        <p>{{character.description}}, {{character.comics.available}}
        </p>
        <div v-for="item in character.comics.items.slice(0, 3)" :key="item.name" >
          <p>{{item.name}}</p>
        </div>
      </div>
      <button @click="showDetail=true" type="button">show</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Character',

  props: {
    character: {
      type: Object,
      required: true
    }
  },

  data() {
    return {
      showDetail: false
    };
  }
}
</script>


<style scoped>

.background {
  background-color: rgb(25, 26, 37);
  color: white;
  width: 20%;
  padding: 0 30px;
}

.images {
  width: 100%;
  height: 200px;
  background-size: cover;
  background-repeat: no-repeat;
}

.firstDetail {
  display: flex;
  flex-direction: column;
  text-align: center;
}

.containerHeroes {
  display: flex;
  flex-direction: column;
}

button {
  background-color: yellow;
}

</style>
