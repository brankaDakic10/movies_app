<template>
    <div class="container mt-4">
        
        <movie-form :movieForm="newMovie" 
         @onSubmit="storeMovie"
         @onReset="resetForm"
        ></movie-form>
        <section class="container mt-4">
        <h4>List of Movies</h4>
        <movie-row v-for="movie in movies" :key="movie.id"
        :movie="movie"></movie-row>
        </section>
    </div>
</template>

<script>
import { moviesService } from '../services/MoviesService'
import MovieForm from './MovieForm.vue'
import MovieRow from './MovieRow.vue'
export default {
    name:'AppMovies',
    components:{
        MovieForm,
        MovieRow
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
