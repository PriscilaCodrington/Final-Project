<script>
import 'vue3-carousel/dist/carousel.css'
import { Carousel, Slide, Pagination } from 'vue3-carousel'
import mainHeader from './components/includes/mainHeader.vue'
import lateralMenu from './components/includes/lateralMenu.vue'
import principalHeader from './components/Parts/principalHeader.vue'


export default{
  name: 'App',
  components:{
    mainHeader,
    lateralMenu,
    principalHeader,
    Carousel,
    Slide,
    Pagination,
   
  }
}
</script>

<template>
  <mainHeader />
  <lateralMenu />
  <principalHeader />
  <carousel :items-to-show="1">
    <!-- <slide v-for="slide in 10" :key="slide">
      {{ slide }}
    </slide> -->

    <template #addons>
      
      <pagination />
    </template>
  </carousel>
</template>

<style>

</style>
