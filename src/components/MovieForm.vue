<template>
    <div class="container mt-4">

     <section class="col-6">
        <h3>Store Movie</h3>

        <b-form @submit.prevent="onSubmit"  @reset="onReset">
  
      <b-form-group label="Movie Title:">
        <b-form-input type="text" v-model="movieForm.title"
        placeholder="Enter title">
        </b-form-input>
      </b-form-group>
      <b-form-group label="Director:">
        <b-form-input type="text" v-model="movieForm.director"
        placeholder="Enter director">
        </b-form-input>
      </b-form-group>
    <b-form-group label="ImageUrl:">
        <b-form-input type="text" v-model="movieForm.imageUrl"
        placeholder="Enter imageUrl">
        </b-form-input>
      </b-form-group>
      <b-form-group label="Duration:">
        <b-form-input type="text" v-model="movieForm.duration"
        placeholder="Enter duration">
        </b-form-input>
      </b-form-group>
 <b-form-group label=" Release Date:">
        <b-form-input type="text" v-model="movieForm.releaseDate"
        placeholder="Enter releaseDate">
        </b-form-input>
      </b-form-group>
<b-form-group label="Genre:">
        <b-form-input type="text" v-model="movieForm.genre"
        placeholder="Enter genre">
        </b-form-input>
      </b-form-group>


      
      
      <b-button type="submit" variant="success">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>

        </b-form>
  </section>


    </div>
</template>

<script>
export default {
 name:'MovieForm',
  props:{
      movieForm:{
        type: Object,
        required:true
      }
     
  },
  methods:{
      onSubmit () {
             this.$emit('onSubmit')
      },
      onReset () {
              this.$emit('onReset')
    }
  }

  
}
</script>

<style>

</style>
