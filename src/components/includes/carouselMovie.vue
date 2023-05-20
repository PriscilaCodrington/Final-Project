<script>
import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel'
import axios from "axios";

export default {
  name: 'carrouselmovie',
  mounted(){
     // invocar los métodos
     this.infoCarousel();
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
      movies:[{}],
    };
  },
  methods: {
    infoCarousel() {
       
      axios
        .get("https://imdb-api.com/en/API/MostPopularMovies/k_gurak224")
        .then((response) => {
            
          for (let i = 1; i < 10; i++) {
          this.info = response.data.items[i];
            console.log(this.info);
            this.id = this.info.id;
            console.log(this.id);
           let moviePoster = this.info.image;
            
           axios

              .get(`https://imdb-api.com/en/API/Trailer/k_gurak224/${this.id}`)
              .then((response) => {
                console.log(response.data);
                let trailerInfo = response.data;
                
                let addNew = {
                    title: trailerInfo.title,
                    year: trailerInfo.year,
                    image: moviePoster,
                    linkTrailer: trailerInfo.linkEmbed, 
                    description: trailerInfo.videoDescription,
                }
                
                this.movies.push(addNew)
                this.movie.shift()
                console.log(this.movies)
              });
          }
        });
    },
  },

}
</script>
<template>
     <carousel :items-to-show="5">
    <slide v-for="movie in movies" :key="movie">
            <img class="posterImage" :src="movie.image" alt="img for movie" />  
            <h2>{{ movie.title }}</h2>
            <!-- <p>{{movie.description }}</p> -->
            <p>{{ movie.year }}</p>
            <!-- <a :href="movie.linkTrailer" target="_blank">Ver video</a> -->
    </slide>

    <template #addons>
      <navigation />
      <pagination />
    </template>
  </carousel>
</template>
<style>
 .posterImage{
    width: 165px;
    height: 224px;
}
</style>