<script >
import axios from "axios";
import { RouterLink, RouterView } from 'vue-router'
import { defineComponent } from "vue"
export default defineComponent({
  name: "mainHeader",
 });
</script>

<template>
  <header class="prinHeader" >
    <div class="contenedor">
     <router-link to='/'><img
          src="../data/img/Artboard 11-8.png"
          alt="principal-logo"
          class="logo"
      /></router-link>
      <RouterLink to="/about" ></RouterLink>
  
      <!-- <input
        type="text"
        id="searchbar"
        name="search"
        placeholder="Search by title..."
        v-model="message"
      /> -->
      <!-- <button type="submit" @click="search()">BUSCAR</button> -->
    </div>
  </header>
  
</template>

<style scoped>
header {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  display: flex;
  justify-content: space-around;
  transition: 0.7s;
  padding: 30px 0;
  z-index: 10;
}
.contenedor {
  width: 90%;
  margin: auto;
}
header .contenedor {
  display: flex;
  justify-content: space-between;
  align-items: center;
}
header .logo {
  position: relative;
  color: #fff;
  font-weight: bold;
  font-size: 2em;
  letter-spacing: 2px;
  transition: 1.5s;
  text-decoration: none;
}

#searchbar {
  padding: 15px 10% 15px 10%;
  border-radius: 10px;
}
</style>
