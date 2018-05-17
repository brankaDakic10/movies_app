<template>
    <div class="container">
        All Movies
        <movie-form :movieForm="newMovie" 
         @onSubmit="storeMovie"
         @onReset="resetForm"
        ></movie-form>
    </div>
</template>

<script>
import { moviesService } from '../services/MoviesService'
import MovieForm from './MovieForm.vue'
export default {
    name:'AppMovies',
    components:{
        MovieForm
    },
    data(){
        return{
         movies:[],
         newMovie:{
            title:'',
            director:'',
            imageUrl:'',
            duration:'',
            releaseDate:'',
            genre:'' 
          }
        }
    },
    methods:{
        storeMovie(){
          moviesService.store(this.newMovie)
    },
        resetForm(){
          return this.newMovie
    }

    },
     beforeRouteEnter (to, from, next) {
          moviesService.getAll()
           .then((response) => {
             next((vm) => {
             vm.movies = response.data
           })
      }).catch((error) => {
        console.log(error)
      })
  }


}
</script>

<style>

</style>
