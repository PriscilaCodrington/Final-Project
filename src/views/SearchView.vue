<script>
import axios from "axios";

export default {
  name: "Home",
  data() {
    return {
      showCompleteInfo: false,
      message: "",
      results: undefined,
      infoCard: undefined,
  
    };
  },
  methods: {
    showInfo(index, showCompleteInfo, id) {
      
      showCompleteInfo = true;
      this.showCompleteInfo = showCompleteInfo;      
      axios
      .get(`https://www.omdbapi.com/?apikey=9d183b39&i=${id}`)
      .then((response) => {console.log(response)
        let trailerInfo =response.data;
       
      let completeCard = {
        nameTitle: trailerInfo.Title,
        yearMovie: trailerInfo.Year,
        descriptionMovie: trailerInfo.Plot,
        posterMovie: trailerInfo.Poster,
        genreMovie: trailerInfo.Genre,
        durationMovie: trailerInfo.Duration,
        directorMovie: trailerInfo.Director,
        actorsMovie: trailerInfo.Actors,
      };
     this.infoCard = completeCard;
    })
      console.log(this.infoCard);
    },
    search() {
      axios
        .get(`https://www.omdbapi.com/?apikey=9d183b39&s=${this.message}`)
        .then((response) => {
          console.log(response.data);
          let info = response.data;
          let arrFilms = info.Search;
          let totalSearch = info.totalResults;
          this.results = arrFilms;
          console.log(this.results);
          console.log(totalSearch);
            
            
        });
    },
  },
};
</script>
<template>
<h1 class="search">Watch anywhere. Cancel anytime ✨.</h1>
  <div class="contenedor">
    
  <input
    type="text"
    id="searchbar"
    name="search"
    placeholder="Search by title..."
    v-model="message"
  />
  <button type="submit" @click="search()" class="btn">🔍 Buscar</button>
</div>
<div class="contenedor">
  <section class="ShowCard" v-for="(movie, index) in results" :key="movie">
    <article @click="showInfo(index, showCompleteInfo, movie.imdbID)">
      <img class="posterImage" :src="movie.Poster" alt="img for movie" />
      <h2 class="title">{{ movie.Title }}</h2>
      <p class="year">{{ movie.Year }} </p>
    </article>
    </section>
  </div>

   <transition name="fadein" v-if="showCompleteInfo">
    <div class="modal-overlay"></div>
  </transition>
  <transition name="fadein"> 
     <div class="modal" v-if="showCompleteInfo">
      <!-- poster  -->
      <div>
        <div class="posterSection">
          <img :src="infoCard.posterMovie" alt="poster-movie" />
        </div>
      </div> 
      <!-- title  -->
      <div>
        <div class="titleCard">
          <h3 class="">{{ infoCard.nameTitle }}</h3>
        </div> 

        <!-- detail section  -->
        <div class="tags">
          <p class="">{{ infoCard.yearMovie }}</p>
          <p class="">{{ infoCard.genreMovie }}</p>
        </div> 

        <!-- description  -->

        <div class="overview">
          <h4>Overview:</h4>
          <p>{{ infoCard.descriptionMovie }}</p>
        </div> 

        <!-- director  -->
        <div class="director">
          <h4>Director:</h4>
          <p class="">{{ infoCard.directorMovie }}</p>
        </div> 
        <!-- actores  -->
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
  width: 70%;
  margin: auto;
  padding-bottom: 20px;
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 20px;
  margin:20px auto;
  padding-top:6px;    
}
#searchbar{ 
  height: 46px;
    border-radius: 48px;
    border: 0.5px solid lightgrey;
    width: 50%;
    padding-right: 40px;
    padding-left: 10px;
    font-size: 15px
}
h1.search{
  margin: 0 auto;
  text-align:center;
  font-weight: 600;
  font-size: 3.12em;
  margin-bottom: 0.4em;

}

.showcard {
  width: 260px;
  height: 368px;
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
h2.title {
 max-width: 50%;
  color: #000;
  margin-top: 1rem;
  overflow: hidden;
  font-size: 1.3rem;
  text-overflow: ellipsis;
  letter-spacing: normal;
  white-space: nowrap;
}
.btn {
  text-decoration: none;
  font-weight: bold;
  font-size: 18px;
  line-height: 1;
  padding: 0.725em 1.25em 0.8em;
  border: 1px #000 solid;
  border-radius: 25px;
}
.btn:hover {
  border: 1px #0d36f0 solid;
  border-radius: 25px;
  background-color: #4bcdff;
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
.modal > div {
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
.modal .closebtn {
  text-decoration: none;
  font-weight: bold;
  font-size: 18px;
  line-height: 1;
  padding: 0.725em 1.25em 0.8em;
  margin-top: 25px;
  border: 1px #000 solid;
  border-radius: 25px;
}
.modal .closebtn:hover {
  border: 1px #0d36f0 solid;
  border-radius: 25px;
  background-color: #4bcdff;
}
fadein-enter {
}
</style>
