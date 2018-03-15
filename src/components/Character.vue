<template>
  <div class="background">
    <div class="containerHeroes">
      <div class="firstDetail">
        <div>
          <h2>
            {{character.name}}
          </h2>
        </div>

        <div>
          <img :src="character.thumbnail.path + '.' + character.thumbnail.extension" alt="">
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
  background-color: rgb(61, 172, 144);
  color: white;
}

.containerHeroes {
  display: flex;
  flex-direction: row;
}

.firstDetail {
  display: flex;
  flex-direction: row;
}

</style>
