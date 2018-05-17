<template>
   <div>
  <b-navbar type="dark" variant="success" toggleable>
    <b-navbar-toggle target="nav_dropdown_collapse"></b-navbar-toggle>
    <b-collapse is-nav id="nav_dropdown_collapse">
      <b-navbar-nav>
        <router-link class="navbar-brand" :to="{name: 'home'}">MoviesApp</router-link>
        <router-link class="nav-item nav-link" :to="{name: 'movies'}">Movies</router-link>
       
      </b-navbar-nav>
    </b-collapse>
  </b-navbar>
</div>

</template>

<script>
export default {

}
</script>

<style>

</style>
