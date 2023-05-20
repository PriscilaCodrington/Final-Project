<script>
import axios from "axios";
import { resolveTransitionHooks } from "vue";
export default {
  //name: "principalHeader",
  mounted(){
     // invocar los métodos
    // this.infoCarusel();
    },
  data() {
    return {
      info: null,
      id: null,
      movies:[{
       
      }],
    };
  },
  
  methods: {
    
  },
};
</script>
<template>
<div>

</div>
   <section v-for="movie in movies" @click="infoHeader"> 
    <img :src="movie.image" alt="img for movie" />  
    <h1>{{ movie.title }} APT</h1>
    <p>{{movie.description }}</p>
    <p>{{ movie.year }}</p>
    <a :href="movie.linkTrailer" target="_blank">Ver video</a>
  </section> 
</template>
<style>

</style>
