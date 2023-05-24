<script scoped>
import searchBar from "../includes/searchBar.vue"
import { ref } from "vue";
import { Carousel, Slide, Pagination, Navigation } from 'vue3-carousel'
import carouselMovie from "../includes/carouselMovie.vue";
export default {
  //name: "principalHeader",
  mounted(){
    
    },
    components: {
    Carousel,
    Slide,
    Pagination,
    Navigation,
	searchBar,
  },
  data() {
    return {
      info: null,
      id: null,

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
                <p class="year">2023    4 season</p>
                <button class="btnPrincipal"> Añadir a Favoritos</button>
                <button class="btnPrincipal"> Mas informacion</button>
            </div>

        </div>
    </main>
 
  
</template>
<style scoped>

.contenedor{
 width: 90%;
margin: auto;
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
.principalMovie .title{
    font-weight: 600;
	font-size: 3.12em;
	margin-bottom: 0.4em;
}
.principalMovie .description {
	font-weight: normal;
	font-size: 1em;
	line-height: 1.75em;
	max-width: 50%;
	margin-bottom: 1.25em;
}
.principalMovie .btnPrincipal {
	background: rgba(0,0,0, 0.5);
	border: none;
	border-radius: 0.31em;
	padding: 0.93em 1.87em;
	color: #fff;
	margin-right: 1.25em;
	cursor: pointer;
	transition: .3s ease all;
	font-size: 1.12em;
}

.principalMovie .btnPrincipal:hover {
	background: #fff;
	color: #000;
}

.principalMovie .year{
font-weight: 600;
font-size: 1em;
padding-bottom: 10px;
top: 5px;

}
/* ---- ----- ----- Media Queries ----- ----- ----- */
@media screen and (max-width: 800px) {
	header .logotipo {
		margin-bottom: 10px;
		font-size: 30px;
	}

	header .contenedor {
		flex-direction: column;
		text-align: center;
	}

	.principalMovie {
		font-size: 14px;
	}

	.principalMovie .description {
		max-width: 100%;
	}
}
</style>
