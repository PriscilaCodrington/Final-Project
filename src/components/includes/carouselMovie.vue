<script>
import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel'
import axios from "axios";
import moviesData from '../data/movies.json'
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
      showCompleteInfo:false,
      movies: moviesData,
    };
  },
  methods: {
    
    // infoCarousel() {
    //     this.movies.pop();
    //   axios
    //     .get("https://imdb-api.com/en/API/MostPopularMovies/k_gurak224")
    //     .then((response) => {
            
    //       for (let i = 1; i < 10; i++) {
    //       this.info = response.data.items[i];
    //         //console.log(this.info);
    //         this.id = this.info.id;
    //         //console.log(this.id);
    //        let moviePoster = this.info.image;
            
    //        axios

    //          .get(`https://www.omdbapi.com/?apikey=9d183b39&i=${this.id}`)
    //           .then((response) => {
    //             //console.log(response.data);
    //             let trailerInfo = response.data;
                
    //             let addNew = {
    //                 title: trailerInfo.Title,
    //                 year: trailerInfo.Year,
    //                 image: trailerInfo.Poster,
    //                 description: trailerInfo.Plot,
    //                 actors: trailerInfo.Actors,
    //                 genre: trailerInfo.Genre,
    //                 duration: trailerInfo.Runtime,

    //             }
                
    //             this.movies.push(addNew)
               

    //             console.log(this.movies)
    //           });
    //       }
    //     });
    // },
  },

}
</script>
<template>
<div class="contenedor">
     <carousel :items-to-show="4" :autoplay="3000" :wrapAround="false">
    <slide  class="ShowCard" v-for="(movie, index) in movies" :key="movie">
            <article @click="showCompleteInfo = true">
            <img class="posterImage" :src="movie.image" alt="img for movie" />  
            <h2 class=title>{{ movie.title }}</h2>
            <!-- <p>{{movie.description }}</p> -->
            <p class="year">{{ movie.year }}</p>
            </article>
            <!-- <a :href="movie.linkTrailer" target="_blank">Ver video</a> -->
    </slide>

    <template #addons>
      <navigation />
      <pagination />
    </template>
  </carousel>
 
  </div> 
  <div class="movieTarget" v-for="(movie, index) in movies">
  <transition name="fadein">
    <div class="modal-overlay" v-if="showCompleteInfo & index"></div>
  </transition>
  <transition name="fadein">
    <div class="modal" v-if="showCompleteInfo">
    <h3> {{movie.title}}</h3>
    <p>{{ movie.year }}</p>
    <button @click="showCompleteInfo = false">X cerrar</button>
</div>
  </transition>
</div>
</template>
<style>
 .contenedor{
width:100vw,

}
article{

    height: 470px;
    border: solid 1px #000;
}
.showcard{
    width: 260px;
    height: 368px;
    margin: 0;
    padding: 0;
    position: relative;
}
 .posterImage{
    width: 260px;
    height: 368px;
    box-shadow: 0px -10px 10px rgba(0, 0, 0, 0.5);
}
.title {
  position: absolute;
  bottom: 50px;
  left: 0;
  right: 0;
  text-align: center;
  color: #000;
}

.year {
  position: absolute;
  bottom: 20px;
  left: 0;
  right: 0;
  text-align: center;
  color: #000;
  }
  .modal-overlay{
    position: absolute;
    top: 0;
    left: 0;
    bottom: 0;
    right: 0;
    z-index: 100;
    background: rgba(0, 0, 0, 0.4);
  }
  .modal{
    position: fixed;
    top:50%;
    left: 50%;
    transform: translate(-50%, -50%);
    background-color: aliceblue;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 3px 3px rgba(0, 0, 0, 0.4);
    z-index: 101;
  }
  fadein-enter{

  }
</style>