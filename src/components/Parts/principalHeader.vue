<script>
import axios from "axios";
import { resolveTransitionHooks } from "vue";
export default {
  //name: "principalHeader",
  mounted(){
     // invocar los métodos
    // this.infoCarusel();
    },
  data() {
    return {
      info: null,
      id: null,
      background:[],
    };
  },
  
  methods: {
    
  },
};
</script>
<template>
<carousel :items-to-show="1">
    <slide v-for="slide in 10" :key="slide">
      {{ slide }}
    </slide>

    <template #addons>
      <navigation />
      <pagination />
    </template>
  </carousel>
</template>   
</template>
<style>

</style>
