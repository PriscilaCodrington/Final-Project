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
    Carousel,
    Slide,
    Pagination,
   
  }
}
</script>

<template>
  <mainHeader />
  <lateralMenu />
  <!-- <principalHeader /> -->
  <carouselMovie />
</template>

<style>

</style>
