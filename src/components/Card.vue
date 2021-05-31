<template>
  <div>
   <ul class="list-group m-3 " >

    <li class="list-group-item">{{card.title}}</li>
    <li class="list-group-item">{{card.original_title || card.original_name}}</li>

    <li v-if="flags.includes(card.original_language)" class="list-group-item">
      <img :src="require(`@/assets/img/${card.original_language}.png`)" :alt="card.original_language">
    </li>
    <li v-else  class="list-group-item">lingua: {{card.original_language}}</li>
    <li class="list-group-item">{{card.original_language}}</li>

    <li class="list-group-item">{{card.vote_average}}</li>
 
  </ul>
  </div>
</template>

<script>
export default {
  name: 'Card',
  //arrey
  data(){
    return{
      flags:['it','en']
    }
  },
  props:{
    card: Object,
  }

}
</script>

<style lang="scss" scoped>


</style>