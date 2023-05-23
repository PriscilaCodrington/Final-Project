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
      background:[ 
    {
    url:" ../data/img/Portada1.png" ,
    title: "Everything Everywhere All at Once",
    year:"2022",
    poster:"https://m.media-amazon.com/images/M/MV5BYTdiOTIyZTQtNmQ1OS00NjZlLWIyMTgtYzk5Y2M3ZDVmMDk1XkEyXkFqcGdeQXVyMTAzMDg4NzU0._V1_Ratio0.7027_AL_.jpg",
    type:"Movie"
},
{
    url:"../data/img/Portada2.png" ,
    title: "Queen Charlotte: A Bridgerton Story",
    year:"2023",
    poster:"https://m.media-amazon.com/images/M/MV5BNWYwNzhhNzMtMWM2Yi00NzdlLTgxNmUtYWI2YTdiNmFmNzQwXkEyXkFqcGdeQXVyMTUzMTg2ODkz._V1_Ratio0.6757_AL_.jpg",
    type:"Serie"
},
{
    url:"../data/img/Portada4.png" ,
    title: "Succession",
    year:"2018 - 2023",
    poster:"https://m.media-amazon.com/images/M/MV5BNWYwNzhhNzMtMWM2Yi00NzdlLTgxNmUtYWI2YTdiNmFmNzQwXkEyXkFqcGdeQXVyMTUzMTg2ODkz._V1_Ratio0.6757_AL_.jpg",
    type: "Serie"
},
{
    url:"../data/img/Portada3.png" ,
    title: "Asteroid City",
    year:"2023",
    poster:"https://m.media-amazon.com/images/M/MV5BNDJmMzY0ZGUtYWE1My00OWViLTg1NTctOWMwZWJlNDQzNGRiXkEyXkFqcGdeQXVyMjkwOTAyMDU../data._V1_Ratio0.6757_AL_.jpg",
    type: "Movie"
}]
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
 
    <main>
        <div class="principalMovie">
            <div class="contenedor">
                <h1 class="title">Succession</h1>
                <p class="description">Follow the lives of the Roy family as they contemplate their future once their aging father begins to step back from the media and entertainment conglomerate they control.</p>
                <p class="year">2023</p> <p class="season">4 season</p>
                <button class="btnPrincipal"> Añadir a Favoritos</button>
                <button class="btnPrincipal"> <i class="fas fa-info-circle" />Mas informacion</button>
            </div>

        </div>
    </main>
 
  
</template>
<style scoped>

.contenedor{
 width: 90%;
 height: 50%;
}
.principalMovie{
    font-size: 16px;
	min-height: 40.62em;
	color: #fff;
	background: linear-gradient(rgba(0, 0, 0, .50) 0%, rgba(0,0,0,.50) 100%), url(../data/img/Portada4.png);
	background-position: center center;
	background-size: cover;
	margin-bottom: 3.12em;
	display: flex;
	align-items: end;}
    .principalMovie .contenedor {
	margin: 0 auto;
	margin-bottom: 6.25em;
}
</style>
