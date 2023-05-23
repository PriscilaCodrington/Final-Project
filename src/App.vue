<script>

import mainHeader from './components/includes/mainHeader.vue'
import lateralMenu from './components/includes/lateralMenu.vue'
import principalHeader from './components/Parts/principalHeader.vue'
import carouselMovie from './components/includes/carouselMovie.vue'

export default{
  name: 'App',
  components:{
    mainHeader,
    lateralMenu,
    principalHeader,
    carouselMovie,
    
   
  }
}
</script>

<template>
  <mainHeader />
  <lateralMenu />
   <principalHeader /> 
  <carouselMovie />
</template>

<style>
*{
	margin: 0;
	padding: 0;
	list-style: none;
	text-decoration: none;
	border: none;
	outline: none;
}
</style>
