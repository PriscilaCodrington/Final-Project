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
      showCompleteInfo:false,
      movies:[  {
            id: "tt6791350",
            "rank": "1",
            "rankUpDown": "0",
            title: "Guardians of the Galaxy Vol. 3",
            "fullTitle": "Guardians of the Galaxy Vol. 3 (2023)",
           year: "2023",
            image: "https://m.media-amazon.com/images/M/MV5BMDgxOTdjMzYtZGQxMS00ZTAzLWI4Y2UtMTQzN2VlYjYyZWRiXkEyXkFqcGdeQXVyMTkxNjUyNQ@@._V1_Ratio0.6716_AL_.jpg",
            "crew": "James Gunn (dir.), Chris Pratt, Chukwudi Iwuji",
            "imDbRating": "8.3",
            "imDbRatingCount": "122644"
        },
        {
            "id": "tt13345606",
            "rank": "2",
            "rankUpDown": "+1",
            title: "Evil Dead Rise",
            "fullTitle": "Evil Dead Rise (2023)",
            year: "2023",
            image: "https://m.media-amazon.com/images/M/MV5BMmZiN2VmMjktZDE5OC00ZWRmLWFlMmEtYWViMTY4NjM3ZmNkXkEyXkFqcGdeQXVyMTI2MTc2ODM3._V1_Ratio0.6716_AL_.jpg",
            "crew": "Lee Cronin (dir.), Mirabai Pease, Richard Crouchley",
            "imDbRating": "6.8",
            "imDbRatingCount": "62145"
        },
        {
            "id": "tt2906216",
            "rank": "3",
            "rankUpDown": "+1",
            title: "Dungeons & Dragons: Honor Among Thieves",
            "fullTitle": "Dungeons & Dragons: Honor Among Thieves (2023)",
           year: "2023",
            image: "https://m.media-amazon.com/images/M/MV5BNmFkN2M2NzItOTY5YS00MmE2LTk3ZjctNTk2YzQ5ZmRiYzJjXkEyXkFqcGdeQXVyMjkwOTAyMDU@._V1_Ratio0.6716_AL_.jpg",
            "crew": "John Francis Daley (dir.), Chris Pine, Michelle Rodriguez",
            "imDbRating": "7.4",
            "imDbRatingCount": "98706"
        },
        {
            "id": "tt4873118",
            "rank": "4",
            "rankUpDown": "+13",
            title: "Guy Ritchie's the Covenant",
            "fullTitle": "Guy Ritchie's the Covenant (2023)",
           year: "2023",
            image: "https://m.media-amazon.com/images/M/MV5BNmQzOWZhOTMtZTcxNC00MTdkLWEwYmUtOWVmOTFhNTdkNjRkXkEyXkFqcGdeQXVyODk2NDQ3MTA@._V1_Ratio0.6716_AL_.jpg",
            "crew": "Guy Ritchie (dir.), Jake Gyllenhaal, Dar Salim",
            "imDbRating": "7.6",
            "imDbRatingCount": "29022"
        },
        {
            "id": "tt15398776",
            "rank": "5",
            "rankUpDown": "+44",
            title: "Oppenheimer",
            "fullTitle": "Oppenheimer (2023)",
           year: "2023",
            image: "https://m.media-amazon.com/images/M/MV5BMDEzNDdjYTctNjA4ZS00ZDgzLTkxNmUtMTQwMzUyMmFhMWRhXkEyXkFqcGdeQXVyMTUzMTg2ODkz._V1_Ratio0.6716_AL_.jpg",
            "crew": "Christopher Nolan (dir.), Cillian Murphy, Emily Blunt",
            "imDbRating": "",
            "imDbRatingCount": "0"
        },
        {
            "id": "tt7405458",
            "rank": "6",
            "rankUpDown": "+39",
            title: "A Man Called Otto",
            "fullTitle": "A Man Called Otto (2022)",
           year: "2022",
            image: "https://m.media-amazon.com/images/M/MV5BNzg3OTEzMTgtYWU0OC00YTI0LWIxOTAtNmRkNTc0Nzg2YWU1XkEyXkFqcGdeQXVyNjY1MTg4Mzc@._V1_Ratio0.7910_AL_.jpg",
            "crew": "Marc Forster (dir.), Tom Hanks, Mariana Treviño",
            "imDbRating": "7.5",
            "imDbRatingCount": "78974"
        },
        {
            "id": "tt6718170",
            "rank": "7",
            "rankUpDown": "-1",
            title: "The Super Mario Bros. Movie",
            "fullTitle": "The Super Mario Bros. Movie (2023)",
           year: "2023",
            image: "https://m.media-amazon.com/images/M/MV5BOTJhNzlmNzctNTU5Yy00N2YwLThhMjQtZDM0YjEzN2Y0ZjNhXkEyXkFqcGdeQXVyMTEwMTQ4MzU5._V1_Ratio0.6716_AL_.jpg",
            "crew": "Aaron Horvath (dir.), Chris Pratt, Anya Taylor-Joy",
            "imDbRating": "7.2",
            "imDbRatingCount": "110711"
        },
        {
            "id": "tt16419074",
            "rank": "8",
            "rankUpDown": "+13",
            title: "Air",
            "fullTitle": "Air (2023)",
           year: "2023",
            image: "https://m.media-amazon.com/images/M/MV5BYmNlOTNlYjUtM2U3Yy00M2ZjLTkxZDQtN2NiNGZiZDI0ZjE3XkEyXkFqcGdeQXVyMTUzMTg2ODkz._V1_Ratio0.6716_AL_.jpg",
            "crew": "Ben Affleck (dir.), Matt Damon, Jason Bateman",
            "imDbRating": "7.5",
            "imDbRatingCount": "62449"
        },
        {
            "id": "tt6968614",
            "rank": "9",
            "rankUpDown": "+371",
            title: "The Mother",
            "fullTitle": "The Mother (2023)",
           year: "2023",
            image: "https://m.media-amazon.com/images/M/MV5BODlmZThjZGItOGRmMC00ODVjLWIzYWMtODBhYzQyZjE4NWE5XkEyXkFqcGdeQXVyMTUzMTg2ODkz._V1_Ratio0.6716_AL_.jpg",
            "crew": "Niki Caro (dir.), Jennifer Lopez, Lucy Paez",
            "imDbRating": "5.5",
            "imDbRatingCount": "19371"
        },
        {
            "id": "tt5971474",
            "rank": "10",
            "rankUpDown": "+5",
            title: "The Little Mermaid",
            "fullTitle": "The Little Mermaid (2023)",
           year: "2023",
            image: "https://m.media-amazon.com/images/M/MV5BYTUxYjczMWUtYzlkZC00NTcwLWE3ODQtN2I2YTIxOTU0ZTljXkEyXkFqcGdeQXVyMTkxNjUyNQ@@._V1_Ratio0.6716_AL_.jpg",
            "crew": "Rob Marshall (dir.), Halle Bailey, Jonah Hauer-King",
            "imDbRating": "",
            "imDbRatingCount": "0"
        },
        {
            "id": "tt9224104",
            "rank": "11",
            "rankUpDown": "+178",
            title: "The Meg 2: The Trench",
            "fullTitle": "The Meg 2: The Trench (2023)",
           year: "2023",
            image: "https://m.media-amazon.com/images/M/MV5BZjAzN2UzNzktNjUyMC00MDhjLTkxNGUtYWRhMzY0MDhiMmNjXkEyXkFqcGdeQXVyODk4OTc3MTY@._V1_Ratio0.6716_AL_.jpg",
            "crew": "Ben Wheatley (dir.), Jason Statham, Jing Wu",
            "imDbRating": "",
            "imDbRatingCount": "0"
        },
        {
            "id": "tt15239678",
            "rank": "12",
            "rankUpDown": "-7",
            title: "Dune: Part Two",
            "fullTitle": "Dune: Part Two (2023)",
           year: "2023",
            image: "https://m.media-amazon.com/images/M/MV5BODI0YjNhNjUtYjM0My00MTUwLWFlYTMtMWI2NGUzYjNjNGQzXkEyXkFqcGdeQXVyMDM2NDM2MQ@@._V1_Ratio0.6716_AL_.jpg",
            "crew": "Denis Villeneuve (dir.), Timothée Chalamet, Zendaya",
            "imDbRating": "",
            "imDbRatingCount": "0"
        },
        {
            "id": "tt13375076",
            "rank": "13",
            "rankUpDown": "-2",
            title: "The Pope's Exorcist",
            "fullTitle": "The Pope's Exorcist (2023)",
           year: "2023",
            image: "https://m.media-amazon.com/images/M/MV5BYjA0MGU4MzYtYTYxMy00MjRhLTlmMDYtZTVhZDc1Y2QwNWY2XkEyXkFqcGdeQXVyMjY5ODI4NDk@._V1_Ratio0.6716_AL_.jpg",
            "crew": "Julius Avery (dir.), Russell Crowe, Daniel Zovatto",
            "imDbRating": "6.1",
            "imDbRatingCount": "30328"
        },
        {
            "id": "tt11358390",
            "rank": "14",
            "rankUpDown": "-4",
            title: "Renfield",
            "fullTitle": "Renfield (2023)",
           year: "2023",
            image: "https://m.media-amazon.com/images/M/MV5BNDIwYjVjMDMtOGYxMy00ZTRiLWE0YzktMjIwYmNhOGE4NGQ4XkEyXkFqcGdeQXVyNjY1MTg4Mzc@._V1_Ratio0.6716_AL_.jpg",
            "crew": "Chris McKay (dir.), Nicholas Hoult, Nicolas Cage",
            "imDbRating": "6.4",
            "imDbRatingCount": "34149"
        },
        {
            "id": "tt2015381",
            "rank": "15",
            "rankUpDown": "+8",
            title: "Guardians of the Galaxy",
            "fullTitle": "Guardians of the Galaxy (2014)",
           year: "2014",
            image: "https://m.media-amazon.com/images/M/MV5BNDIzMTk4NDYtMjg5OS00ZGI0LWJhZDYtMzdmZGY1YWU5ZGNkXkEyXkFqcGdeQXVyMTI5NzUyMTIz._V1_Ratio0.6716_AL_.jpg",
            "crew": "James Gunn (dir.), Chris Pratt, Vin Diesel",
            "imDbRating": "8.0",
            "imDbRatingCount": "1212793"
        },],
    };
  },
  methods: {
    
    infoCarousel() {
        this.movies.pop();
      axios
        //.get("https://imdb-api.com/en/API/MostPopularMovies/k_gurak224")
        .then((response) => {
            
          for (let i = 1; i < 20; i++) {
          this.info = response.data.items[i];
            console.log(this.info);
            this.id = this.info.id;
            console.log(this.id);
           let moviePoster = this.info.image;
            
           axios

              //.get(`https://imdb-api.com/en/API/Trailer/k_gurak224/${this.id}`)
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
               

                console.log(this.movies)
              });
          }
        });
    },
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