<template>
  <div id="app">

    <Header 
    @startSearch="startSearch"
    />

    <Main v-if="results.movie.length > 0" type="movie" :list="results.movie" />
    <Main v-if="results.tv.length > 0" type="tv" :list="results.tv" />

    <Card />


  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue';
import Main from './components/Main.vue';
import Card from './components/Card.vue';

export default {
  name: 'App',
  components: {
    Header,
    Main,
    Card,
  },

  data(){
    return{
        apiUrl: 'https://api.themoviedb.org/3/search/',
        apiKey: '1b3eb153fce73eb6b953f7d515b2dc1d',
        results:{
          'movie':[],
          'tv':[],
        }

    }
  },

  methods:{

    startSearch(obj){
      //console.log(obj);
      this.resetResults();

      if(obj.type === 'all'){
        this.getAPI(obj.text, 'movie');
        this.getAPI(obj.text, 'tv');
      }else{
        this.getAPI(obj.text, obj.type)
      }

    },

    resetResults(){
      this.results.movie = [];
      this.results.tv = [];
    },

    getAPI(query, type){
      axios.get(this.apiUrl+type,{
        params:{
          api_key: this.apiKey,
          query: query,
          language: 'it-IT'

        }

      })
      .then(res => {
        this.results[type] = res.data.results;
        console.log(res.data);
      })
      .catch(err => {
        console.log(err);
      })
    },
  

  },
    created(){
      
    }


  





}
</script>

<style lang="scss">
@import './assets/styles/general';


</style>
