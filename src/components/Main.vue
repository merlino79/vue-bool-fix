<template>
  <main class="container">
    <h1>
      {{titles[type]}}
    </h1>
    {{list.length}}
  </main>
</template>

<script>
export default {
  name: 'Main',
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