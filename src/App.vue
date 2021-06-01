<template>
  <div id="app">
    <!-- emit header  con funzione startSearch-->
    <Header 
    @startSearch="startSearch"
    />
    <!-- in assenza di risultati  -->
    <h3 v-if="results.movie.length === 0 && results.tv.length === 0 ">
      nessun risultato trovato
    </h3>
    <!-- 2 componenti movie e tv  -->
    <!-- passo 2 props: tipo dato e elenco risultati -->
    <Main v-if="results.movie.length > 0" type="movie" :list="results.movie" />
    <Main v-if="results.tv.length > 0" type="tv" :list="results.tv" />

    


  </div>
</template>

<script>
import axios from 'axios';
import Header from './components/Header.vue';
import Main from './components/Main.vue';


export default {
  name: 'App',
  components: {
    Header,
    Main,
    
  },

  data(){
    return{
        apiUrl: 'https://api.themoviedb.org/3/search/',
        apiKey: '1b3eb153fce73eb6b953f7d515b2dc1d',
        //nel mio oggetto memorizzo le due ricerche..
        results:{
          'movie':[],
          'tv':[],
        }

    }
  },

  methods:{
    //lancio la ricerca
    startSearch(obj){
      //console.log(obj);
      this.resetResults();
        //resetto le ricerche salvate e se cerca tutto fa le due chiamate 
      if(obj.type === 'all'){
        this.getAPI(obj.text, 'movie');
        this.getAPI(obj.text, 'tv');
      }else{
        this.getAPI(obj.text, obj.type)
      }

    },

    resetResults(){
      //memorizzo le ricerche in un array
      this.results.movie = [];
      this.results.tv = [];
    },
    //getApi funzione chiamata axios
    getAPI(query, type){

      if(query !== ''){ //controllo della chiamata avviene solo se premo il pulsante
         axios.get(this.apiUrl+type,{
        params:{
          api_key: this.apiKey,
          query: query,
          language: 'it-IT'

        }

      })
      .then(res => {

        // in base al tipo di ricerca salvo il dato nell'array dell'oggetto results 
        this.results[type] = res.data.results;
        //console.log(res.data);
      })
      .catch(err => {
        console.log(err);
      })
        
      }
     
    },
  

  },
    created(){
      let type = 'movie'
      axios.get('https://api.themoviedb.org/3/search/movie?api_key=b29024d524a40cb95e8ebc16787d55cf&query=arsenè&language= it-IT',{
        params:{
            api_key: this.apiKey,
            language: 'it-IT'
          }
        })
        .then(res => {
           this.results[type] = res.data.results;
        })
        .catch(err => {
          console.log(err);

      })
      
    }


  





}
</script>

<style lang="scss">
@import './assets/styles/general';


</style>
