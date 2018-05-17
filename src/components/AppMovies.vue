<template>
    <div class="container mt-4">
        
        <movie-form :movieForm="newMovie" 
         @onSubmit="storeMovie"
         @onReset="resetForm"
        ></movie-form>
        <section class="container mt-4">
        <h4>List of Movies</h4>
        
        <movie-search @search-term-change="onSearchTermChanged"></movie-search>
        <br>
        <input class="form-control" v-model="searchTerm" type="text" placeholder="Search movie title"/>


        
        
        <movie-row v-for="movie in filterProducts" :key="movie.id"
        :movie="movie"></movie-row>
       
        <div  v-if="!filterProducts.length" class="alert alert-danger" role="alert">
             This movie title is not included in the list of movies!
        </div>
        </section>
    </div>
</template>

<script>
import { moviesService } from '../services/MoviesService'
import MovieForm from './MovieForm.vue'
import MovieRow from './MovieRow.vue'
import MovieSearch from './MovieSearch.vue'
export default {
    name:'AppMovies',
    components:{
        MovieForm,
        MovieRow,
        MovieSearch
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
          },
          searchTerm:''
        }
    },
    methods:{
        storeMovie(){
          moviesService.store(this.newMovie)
    },
        resetForm(){
          return this.newMovie
    },
     onSearchTermChanged(term) {
          moviesService.getAll(term)
            .then(({ data }) => {
           this.movies = data
        })
       },

    },
    computed:{
   filterProducts(){
       return this.movies.filter(movie =>{
           return movie.title.toLowerCase().startsWith(this.searchTerm.toLowerCase())
       })
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
