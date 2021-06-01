<template>
  <header>
    
       
    
   <div class="container d-flex pt-4">
     <div class="logo">
       <div class="txt">
          bool-fix
       </div>
      
     </div>
     <!-- testo da cercare -->
     <div class="flex-grow-1  ">
       <input
       v-model.trim= "textToSearch"
       placeholder="search...."
       class="form-control "
        type="text">
     </div>
     <!-- evento -->
     <!-- emit invio due parametri: evento e ricerva film o serie -->
     <div>
        <button
        @click="sendEmit('movie')"
        class="btn btn-primary ms-3">cerca film</button>

     </div>
     <div>
        <button
        @click="sendEmit('tv')"
        class="btn btn-primary ms-3">cerca serie</button>

     </div>
     <div>
        <button
        @click="sendEmit('all')"
        class="btn btn-primary ms-3">cerca tutto</button>

     </div>
    
   </div>
   
  
  </header>
</template>

<script>
export default {
  name: 'Header',

  data(){
    return{
      textToSearch: ''
    }

  },
  methods:{
    sendEmit(type){
      this.$emit('startSearch',{text:this.textToSearch, type:type})

    }
  },

}
</script>

<style lang="scss" scoped>
    @import '../assets/styles/vars.scss';
header{
  height: 100px;
  background-color:$brand-color ;
  .logo{
    width: 100px;
    .txt{
      color: red;
    }

  }

 
}




</style>