<script>
import axios from "axios";


export default{
  name: 'Home',
  data(){
   return{
     message:"",
    results: undefined}
  },
  methods:{
   
    search(){
      axios
      .get(`https://www.omdbapi.com/?apikey=9d183b39&s=${this.message}`)
      .then((response) =>{ 
        console.log(response.data)
        let info = response.data;
        let arrFilms = info.Search;
        let totalSearch= info.totalResults;
          this.results =arrFilms;
        console.log(this.results);
      console.log(totalSearch);
      })
    }
  }}
</script>
<template>
    <input type="text" id="searchbar" name="search" placeholder="Search by title..." v-model="message" >
      <button type="submit" @click="search()">BUSCAR</button>

      <section  class="ShowCard" v-for="movie in results" :key="movie">
            <article @click="showCompleteInfo = true">
            <img class="posterImage" :src="movie.Poster" alt="img for movie" />  
            <h2 class=title>{{ movie.Title }}</h2>
            <!-- <p>{{movie.description }}</p> -->
            <p class="year">{{ movie.Year }}</p>
            </article>
            <!-- <a :href="movie.linkTrailer" target="_blank">Ver video</a> -->
          </section>
</template>
<style>

</style>
