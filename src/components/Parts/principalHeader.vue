<script>
import axios from "axios";
export default {
  name: "principalHeader",
  onmount(){
    
  },
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
        .get("https://imdb-api.com/en/API/Top250Movies/k_gurak224")
        .then((response) => {
            this.movies.pop()
          for (let i = 1; i < 7; i++) {
            this.info = response.data.items[i];
            console.log(this.info);
            this.id = this.info.id;
            console.log(this.id);
            axios
              .get(`https://imdb-api.com/en/API/Trailer/k_gurak224/${this.id}`)
              .then((response) => {
                console.log(response.data);
                let trailerInfo = response.data;
                
                let addNew = {title: trailerInfo.title,
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
    <v-img :src="movie.image" />  
    <h1>{{ movie.title }} APT</h1>
    <p>{{movie.description }}</p>
    <p>{{ movie.year }}</p>
    <button type="submit" :src="movie.linkTrailer">Ver video</button>
  </section>
</template>
<style>
section #carrusel-contenido {
  padding: 50%;
  margin: 50%;
  background-color: #000;
}
</style>
