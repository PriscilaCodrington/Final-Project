<script>
import axios from "axios";

export default {
  name: "Home",
  data() {
    return {
      message: "",
      results: undefined,
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
<h1 class="search">Search here</h1>
  <div class="contenedor">
    
  <input
    type="text"
    id="searchbar"
    name="search"
    placeholder="Search by title..."
    v-model="message"
  />
  <button type="submit" @click="search()" class="btn">Buscar</button>
</div>
<div class="contenedor">
  <section class="ShowCard" v-for="movie in results" :key="movie">
    <article @click="showCompleteInfo = true">
      <img class="posterImage" :src="movie.Poster" alt="img for movie" />
      <h2 class="title">{{ movie.Title }}</h2>
      <!-- <p>{{movie.description }}</p> -->
      <p class="year">{{ movie.Year }}</p>
    </article>
    </section>
  </div>
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
</style>
