<template>
<div class="container mt-4">
     <section
    class="row" >
    <div class="col-sm" v-text="movie.id"></div>
    <div class="col-sm" v-text="movie.title"></div>
    <div class="col-sm" v-text="movie.director"></div>
    <div class="col-sm" v-text="movie.genre"></div>
    <div class="col-sm" v-text="movie.releaseDate"></div>
    <div class="col-sm" v-text="movie.duration"></div> 
    
     </section>
  </div>
</template>

<script>
export default {
  name:'MovieRow',
  props:{
      movie:{
       type: Object,
       required:true
      }
     
  }
 
}
</script>

<style>

</style>
