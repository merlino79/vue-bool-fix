<template>
  <div>
   <ul class="list-group m-3 " >
  <li class="list-group-item">{{card.title}}</li>
  <li class="list-group-item">{{card.original_title || card.original_name}}</li>
  <li class="list-group-item">{{card.original_language}}</li>
  <li class="list-group-item">{{card.vote_average}}</li>
 
</ul>
  </div>
</template>

<script>
export default {
  name: 'Card',
  props:{
    card: Object
  }

}
</script>

<style lang="scss" scoped>


</style>