<script>
import axios from "axios";
export default {
  //name: "principalHeader",
  
  data() {
    return {
      info: null,
      id: null,
      movies:[{}],
    };
  },
  
  methods: {
    infoHeader() {
      axios
        .get("https://imdb-api.com/en/API/MostPopularMovies/k_gurak224")
        .then((response) => {
            
          for (let i = 27; i < 32; i++) {
          this.info = response.data.items[i];
            console.log(this.info);
            this.id = this.info.id;
            console.log(this.id);
            axios
              .get(`https://imdb-api.com/en/API/Trailer/k_gurak224/${this.id}`)
              .then((response) => {
                console.log(response.data);
                let trailerInfo = response.data;
                
                let addNew = {
                    title: trailerInfo.title,
                    year: trailerInfo.year,
                    image: trailerInfo.thumbnailUrl,
                    linkTrailer: trailerInfo.linkEmbed, 
                    description: trailerInfo.videoDescription,
                }
                
                this.movies.push(addNew)
                
                console.log(this.movies)
              });
          }
        });
    },
  },
};
</script>
<template>

  <section id="carrusel-contenido" v-for="movie in movies" @click="infoHeader"> 
    <img :src="movie.image" alt="img for movie" />  
    <h1>{{ movie.title }} APT</h1>
    <p>{{movie.description }}</p>
    <p>{{ movie.year }}</p>
    <a :href="movie.linkTrailer" target="_blank">Ver video</a>
  </section>
</template>
<style>

</style>
