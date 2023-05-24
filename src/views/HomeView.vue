<script >
import carouselSeries from '../components/includes/carouselSeries.vue';
import mainHeader from '../components/includes/mainHeader.vue'
import principalHeader from '../components/Parts/principalHeader.vue'
import carouselMovieVue from '../components/includes/carouselMovie.vue';
import footerVue from '../components/includes/footer.vue';
import SearchView from './SearchView.vue';
export default{
  name: 'Home',
  components:{
    mainHeader,
    principalHeader,
    carouselMovieVue,
    carouselSeries,
    footerVue,
    SearchView,
  }}
</script>

<template>
  <main>
    <mainHeader/>
    <principalHeader />
    <SearchView/>
    <carouselMovieVue />
    <carouselSeries />
    <footerVue />
  </main>

</template>
