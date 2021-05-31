<template>
  <header>
   <div class="container d-flex pt-4">
     <div class="flex-grow-1  ">
       <input
       v-model.trim= "textToSearch"
       placeholder="search...."
       class="form-control "
        type="text">
     </div>
     <div>
        <button
        @click="$emit('startSearch',{text:textToSearch, type:'movie'})"
        class="btn btn-primary ms-3">cerca film</button>

     </div>
     <div>
        <button
        @click="$emit('startSearch',{text:textToSearch, type:'tv'})"
        class="btn btn-primary ms-3">cerca serie</button>

     </div>
     <div>
        <button
        @click="$emit('startSearch',{text:textToSearch, type:'all'})"
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
      textToSearch: 'ritorno al futuro'
    }

  }

}
</script>

<style lang="scss" scoped>
  //  @import '../assets/styles/vars.scss';
header{
  height: 100px;
  background-color:rgb(78, 75, 75) ;

 
}




</style>