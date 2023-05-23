<script>
import headerData from "../data/header.json"
import { ref } from "vue";
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel'
export default {
  //name: "principalHeader",
  mounted(){
    
    },
    components: {
    Carousel,
    Slide,
    Pagination,
    Navigation,
  },
  data() {
    return {
      info: null,
      id: null,
      background:ref( [ 
    {
    url:require("@/img/Portada1.png") ,
    title: "Everything Everywhere All at Once",
    year:"2022",
    poster:"https://m.media-amazon.com/images/M/MV5BYTdiOTIyZTQtNmQ1OS00NjZlLWIyMTgtYzk5Y2M3ZDVmMDk1XkEyXkFqcGdeQXVyMTAzMDg4NzU0._V1_Ratio0.7027_AL_.jpg",
    type:"Movie"
},
{
    url:"@/img/Portada2.png" ,
    title: "Queen Charlotte: A Bridgerton Story",
    year:"2023",
    poster:"https://m.media-amazon.com/images/M/MV5BNWYwNzhhNzMtMWM2Yi00NzdlLTgxNmUtYWI2YTdiNmFmNzQwXkEyXkFqcGdeQXVyMTUzMTg2ODkz._V1_Ratio0.6757_AL_.jpg",
    type:"Serie"
},
{
    url:"@/img/Portada4.png" ,
    title: "Succession",
    year:"2018 - 2023",
    poster:"https://m.media-amazon.com/images/M/MV5BNWYwNzhhNzMtMWM2Yi00NzdlLTgxNmUtYWI2YTdiNmFmNzQwXkEyXkFqcGdeQXVyMTUzMTg2ODkz._V1_Ratio0.6757_AL_.jpg",
    type: "Serie"
},
{
    url:"@/img/Portada3.png" ,
    title: "Asteroid City",
    year:"2023",
    poster:"https://m.media-amazon.com/images/M/MV5BNDJmMzY0ZGUtYWE1My00OWViLTg1NTctOWMwZWJlNDQzNGRiXkEyXkFqcGdeQXVyMjkwOTAyMDU@._V1_Ratio0.6757_AL_.jpg",
    type: "Movie"
}])
      ,
    };
  },
  
  methods: {
    principalHeader(){
           }
  },
};
</script>
<template>
<carousel :items-to-show="1">
    <slide v-for="slide in background" :key="slide">
        <img :src="require(slide.src)" alt="Header">
      {{ slide.title }}
      {{ slide.year }}
      {{ slide.type }}
        
     
    </slide>    <template #addons>
      <navigation />
      <pagination />
    </template>
  </carousel>
  
</template>
<style></style>
