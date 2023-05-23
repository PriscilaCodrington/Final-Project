<script>
export default{
 name: 'mainHeader',
 methods:{
   scrollHeader(){
      alert('hola')
      let header = document.querySelector('header');
      header.classList.add("down")
   }
 }
}
</script>

<template>
   <header class="prinHeader" @click="scrollHeader()" >
      <a href="#"><img src="../data/img/Artboard 11-8.png" alt="principal-logo" class="logo" /></a>
      <input type="text" id="searchbar" name="search" placeholder="Search by title..." >
      <div class="account">
         <img src="#" alt="" srcset="">
         <span>Mi cuenta</span>
      </div>
   </header>
   
</template>
  
<style scoped>

  header{
      position: fixed;
      top: 0;
      left: 0;
      width: 100%;
      display: flex;
      justify-content: space-around;
      transition: 0.7s;
      padding: 30px 20px;
      z-index: 10;
      background-color: #fff;
  }
   header .logo{
      position: relative;
      color: #fff;
      font-weight: bold;
      font-size: 2em;
      letter-spacing: 2px;
      transition: 1.5s;
      text-decoration: none;
   }

   #searchbar{
     padding:15px 10% 15px 10%;
     border-radius: 10px;
   }
</style>
  