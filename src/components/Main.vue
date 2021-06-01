<template>
  <main class="container">
    <div class="d">
       <!-- <h1>
      {{titles[type]}}
    </h1> -->
  
      <div class="d-flex flex-wrap   ">
         <Card 
      v-for="card in list"
      :key="card.id"
      :card="card"
      />
      </div>

    </div>
   
     
   
  </main>
  
</template>

<script>
import Card from '../components/Card.vue';
export default {
  name: 'Main',
  components:{
    Card
  },
  props:{
    type: String,
    list: Array,

  },

  data(){

    return{
      titles:{
        'movie': 'film trovati',
        'tv': 'serie tv trovate'
      }
    }
  }

}
</script>

<style lang="scss" scoped>

</style>