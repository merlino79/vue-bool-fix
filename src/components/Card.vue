<template>
  <div>
     <div class="flip-card">
      <div class="flip-card-inner">
       <div class="flip-card-front">
           <img src="img_avatar.png" alt="Avatar" style="width:300px;height:300px;">
         </div>
    <div class="flip-card-back">
      <h1>John Doe</h1>
      <p>Architect & Engineer</p>
      <p>We love that guy</p>
    </div>
  </div>
</div> 



   <!-- <ul class="list-group m-3 " >

    <li class="list-group-item">{{card.title || card.name}}</li>
    <li class="list-group-item">{{card.original_title || card.original_name}}</li>

    <li v-if="flags.includes(card.original_language)" class="list-group-item">

      <img :src="require(`@/assets/img/${card.original_language}.png`)" :alt="card.original_language">
    </li>

    <li v-else  class="list-group-item">lingua: {{card.original_language}}</li>
    
    <li class="list-group-item">{{card.original_language}}</li>

    <li class="list-group-item">{{card.vote_average}}</li>
 
  </ul> -->
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
.flip-card {
  background-color: transparent;
  width: 300px;
  height: 200px;
  border: 1px solid #f1f1f1;
  perspective: 1000px; /* Remove this if you don't want the 3D effect */
}

/* This container is needed to position the front and back side */
.flip-card-inner {
  position: relative;
  width: 100%;
  height: 100%;
  text-align: center;
  transition: transform 0.8s;
  transform-style: preserve-3d;
}

/* Do an horizontal flip when you move the mouse over the flip box container */
.flip-card:hover .flip-card-inner {
  transform: rotateY(180deg);
}

/* Position the front and back side */
.flip-card-front, .flip-card-back {
  position: absolute;
  width: 100%;
  height: 100%;
  -webkit-backface-visibility: hidden; /* Safari */
  backface-visibility: hidden;
}

/* Style the front side (fallback if image is missing) */
.flip-card-front {
  background-color: #bbb;
  color: black;
}

/* Style the back side */
.flip-card-back {
  background-color: dodgerblue;
  color: white;
  transform: rotateY(180deg);
}


</style>