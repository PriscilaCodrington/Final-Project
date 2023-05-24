<script >

import mainHeader from '../components/includes/mainHeader.vue'
import principalHeader from '../components/Parts/principalHeader.vue'
import carouselMovieVue from '../components/includes/carouselMovie.vue';
import footerVue from '../components/includes/footer.vue';
export default{
  name: 'Home',
  components:{
    mainHeader,
    principalHeader,
    carouselMovieVue,
    footerVue
  }}
</script>

<template>
  <main>
    <mainHeader/>
    <principalHeader />
    <carouselMovieVue />
    <footerVue />
  </main>

</template>
