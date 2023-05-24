<script>
import "vue3-carousel/dist/carousel.css";
import { Carousel, Slide, Pagination, Navigation } from "vue3-carousel";
import axios from "axios";

import moviesData from "../data/movies.json";

export default {
  name: "carrouselmovie",
  mounted() {
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
      showCompleteInfo: false,
      infoCard: {},
      movies: [{}],
    };
  },
  methods: {
    showInfo(index, showCompleteInfo) {
      console.log(index);
      console.log(showCompleteInfo);
      showCompleteInfo = true;
      this.showCompleteInfo = showCompleteInfo;
      let completeCard = {
        nameTitle: this.movies[index].title,
        yearMovie: this.movies[index].year,
        descriptionMovie: this.movies[index].description,
        posterMovie: this.movies[index].image,
        genreMovie: this.movies[index].genre,
        durationMovie: this.movies[index].duration,
        directorMovie: this.movies[index].director,
        actorsMovie: this.movies[index].actors,
      };
      this.infoCard = completeCard;
      console.log(this.infoCard);
    },
    infoCarousel() {
      this.movies.pop();
      axios
        .get("https://imdb-api.com/en/API/MostPopularMovies/k_ofp6bn11")
        .then((response) => {
          for (let i = 1; i < 10; i++) {
            this.info = response.data.items[i];

            this.id = this.info.id;

            axios
              .get(`https://www.omdbapi.com/?apikey=9d183b39&i=${this.id}`)
              .then((response) => {
                let trailerInfo = response.data;

                let addNew = {
                  title: trailerInfo.title || trailerInfo.Title,
                  year: trailerInfo.year || trailerInfo.Year,
                  image: trailerInfo.poster || trailerInfo.Poster,
                  description: trailerInfo.plot || trailerInfo.Plot,
                  genre: trailerInfo.genre || trailerInfo.Genre,
                  duration: trailerInfo.runtime || trailerInfo.Runtime,
                  director: trailerInfo.director || trailerInfo.Director,
                  actors: trailerInfo.actors || trailerInfo.Actors,
                };

                this.movies.push(addNew);

                console.log(this.movies);
              });
          }
        });
    },
  },
};
</script>
<template>
  <div class="contenedor">
    <h1 class="titlePrincipal">Movies</h1>

    <carousel :items-to-show="4" autoplay="4000" :wrapAround="true">
      <slide class="ShowCard" v-for="(movie, index) in movies" :key="index">
        <article @click="showInfo(index, showCompleteInfo)">
          <img class="posterImage" :src="movie.image" alt="img for movie" />
          <h2 class="title">{{ movie.title }}</h2>
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

  <transition name="fadein" v-if="showCompleteInfo">
    <div class="modal-overlay"></div>
  </transition>
  <transition name="fadein">
    <div class="modal" v-if="showCompleteInfo">
      <!-- poster -->
      <div>
      <div class="posterSection">
        <img :src="infoCard.posterMovie" alt="poster-movie" />
      </div>
    </div>
      <!-- title -->
    <div>
        <div class="titleCard">
          <h3 class="">{{ infoCard.nameTitle }}</h3>
        </div>
     
        <!-- detail section -->
        <div class="tags">
          <p class="">{{ infoCard.yearMovie }}</p>
          <p class="">{{ infoCard.genreMovie }}</p>
       </div>
      
      <!-- description -->

      <div class="overview">
        <h4>Overview:</h4>
        <p>{{ infoCard.descriptionMovie }}</p>
      </div>
   
    
      <!-- director -->
      <div class="director">
        <h4>Director:</h4>
        <p class="">{{ infoCard.directorMovie }}</p>
      </div>
      <!-- actores -->
      <div class="actors">
        <h4>Actors:</h4>
        <p class="">{{ infoCard.actorsMovie }}</p>
      </div>
    </div>
      <button class="closebtn" @click="showCompleteInfo = false">✖️ Cerrar</button>
    </div>
  </transition>
</template>
<style scoped>
.contenedor {
  width: 90%;
  margin: auto;
  z-index: 10;
}
.contenedor .titlePrincipal {
  font-weight: 600;
  font-size: 3.12em;
  margin-bottom: 0.4em;
}
article {
  height: 470px;
}
.showcard {
  width: 260px;
  height: 368px;
  margin: 0;
  padding: 0;
  position: relative;
}
.posterImage {
  width: 260px;
  height: 368px;
}
.posterImage:hover,
.posterImage:focus {
  transform: scale(1.02);
}
.title {
  position: absolute;
  bottom: 50px;
  left: 0;
  right: 0;
  text-align: center;
  color: #000;
  margin-top: 1rem;
  overflow: hidden;
  font-size: 1.3rem;
  text-overflow: ellipsis;
  letter-spacing: normal;
  white-space: nowrap;
}

.year {
  position: absolute;
  bottom: 20px;
  left: 0;
  right: 0;
  text-align: center;
  color: #000;
}
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  z-index: 100;
  background: rgba(0, 0, 0, 0.4);
  min-height: 100vh;
}
.modal {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  background: #f9f7e8;
  padding: 20px;
  border-radius: 10px;
  box-shadow: 0 4px 16px rgba(0, 0, 0, 0.1);
  z-index: 8000;
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  align-items: stretch;
  transition: all 0.1s cubic-bezier(0.455, 0.03, 0.515, 0.955);
  margin: 0 auto;
  width: 90%;
  max-width: 1280px;
  max-height: 95vh;
  
  overflow: auto;
}
.modal > div{
  width: 50%;
}
.modal .titleCard {
  font-size: 1.3rem;
  font-weight: bold;
  margin-top: 25px;
  text-align: center;
}
.modal .tags {
  display: inline-flex;
  margin: 0 auto;
}
.modal .tags p {
  font-size: 18px;
  padding: 10px;
}
.modal .actors,
.director {
  margin-top: 20px;
}
.modal .actors h4,
.director h4 {
  font-weight: 600;
  font-size: 14px;
}
.modal .actors h4,
.director p {
  font-size: 14px;
}

.modal .overview {
  margin-top: 20px;
}
.modal .overview h4 {
  font-weight: 600;
  font-size: 18px;
}
.modal .overview p {
  font-size: 16px;
  line-height: 24px;
}
.modal .posterSection {
  border-radius: 10px;
  display: flex;
  justify-content: center;
}
.modal .closebtn{
  text-decoration: none;
	font-weight: bold;
  font-size: 18px;
	line-height: 1;
  padding: 0.725em 1.25em 0.8em;
  margin-top: 25px;
  border: 1px #000 solid;
  border-radius: 25px;

}
.modal .closebtn:hover{
  
  border: 1px #0d36f0 solid;
  border-radius: 25px;
  background-color: #4bcdff;
}
fadein-enter {
}
</style>
