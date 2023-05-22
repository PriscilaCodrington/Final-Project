<script >
import mainHeader from '../components/includes/mainHeader.vue'
import principalHeader from '../components/Parts/principalHeader.vue'
import carouselMovieVue from '../components/includes/carouselMovie.vue';

export default{
  name: 'Home',
  components:{
    mainHeader,
    principalHeader
  }}
</script>

<template>
  <main>
    <mainHeader/>
    <principalHeader />
  </main>

</template>
