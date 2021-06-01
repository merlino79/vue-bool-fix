<template>
  <div class="p-3 col-md-6 col-lg-4 col-md-3 ">
     <div class="flip-card">
      <div class="flip-card-inner">
       <div class="flip-card-front">
           <img class=" " :src="imageURL+card.poster_path" :alt="card.title || card.name" >
         </div>
    <div class="flip-card-back">
     <p class="mt-3 ">
       <strong>Titolo:</strong>
       {{card.title || card.name}}
     </p>
     <p class="">
       <strong>Titolo Originale:</strong>
       {{card.original_title || card.original_name}}
     </p>

    <div>

       
      
 
     <div class="stars">
       <div class="empty">
                <div class="inner">
                  <i class="far fa-star"></i>
                  <i class="far fa-star"></i>
                  <i class="far fa-star"></i>
                  <i class="far fa-star"></i>
                  <i class="far fa-star"></i>
                </div>
        </div>
        <div class="solid" :style="`width:${6.7*card.vote_average}px`" >
                <div class="inner">
                  <i class="fas fa-star"></i>
                  <i class="fas fa-star"></i>
                  <i class="fas fa-star"></i>
                  <i class="fas fa-star"></i>
                  <i class="fas fa-star"></i>
                </div>
        </div>
     </div>
    </div>
      
     <p class="">
       <strong>lingua: </strong>
      
       <img  class="flag"
       v-if="flags.includes(card.original_language)" 
       :src="require(`@/assets/img/${card.original_language}.png`)" :alt="card.original_language">
       <span v-else>
          {{card.original_language}}
       </span>
     </p>
      <p >
       <strong class="color">Recensione: </strong>
       {{card.overview}}
     </p>

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
      flags:['it','en'],
      imageURL: 'https://image.tmdb.org/t/p/w342'
    }
  },
  props:{
    card: Object,
  }

}
</script>

<style lang="scss" scoped>
.flag{
  width: 30px;
}
.flip-card {
  background-color: transparent;
  width: 342px;
  height: 513px;
  // border: 1px solid #d12525;
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
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  font-size: 0.75rem;
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
   background-color: #202020;
  border: 1px solid rgb(176, 172, 172);
  cursor: pointer;
}

/* Style the front side (fallback if image is missing) */
.flip-card-front {
  background-color: #bbb;
  color: black;
  img{
    width: 100%;
  }
}

/* Style the back side */
.flip-card-back {
  background-color: rgb(64, 65, 66);
  color: white;
  transform: rotateY(180deg);
  .color{
    color: rgb(248, 196, 176);
  }
  .inner[data-v-54cdc180] {
    width: 68px;
    color: rgb(233, 233, 178);
}

  //star position

  .stars{
   position: relative;
   .empty, .solid{
     position: absolute;
     top: -18px;
     left: 136px;
     overflow: hidden;
   }
   .inner{
     width: 68px;
   }
  }
}


</style>