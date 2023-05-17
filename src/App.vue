<script>
import mainHeader from './components/includes/mainHeader.vue'
import lateralMenu from './components/includes/lateralMenu.vue'
import principalHeader from './components/Parts/principalHeader.vue'

export default{
  name: 'App',
  components:{
    mainHeader,
    lateralMenu,
    principalHeader
  }
}
</script>

<template>
  <mainHeader />
  <lateralMenu />
  <principalHeader />
  
</template>

<style>

</style>
