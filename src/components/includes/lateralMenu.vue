<script>

export default{
 name: 'lateralMenu',
 
 methods:{
   
 }
}
</script>

<template>
    <section class="vertical-bar">
        <a href="#"><i class="fa fa-icon1"></i></a>
        <a href="#"><i class="fa fa-icon2"></i></a>
        <a href="#"><i class="fa fa-icon3"></i></a>
    </section>   
</template>
  
<style scoped>
.vertical-bar {
  position: fixed;
  top: 50%;
  left: 0;
  transform: translateY(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  width: 60px; /* Ajusta el ancho según tus necesidades */
  height:50%; /* Ajusta la altura según tus necesidades */
  background-color: #F4F6F6; /* Ajusta el color de fondo según tus necesidades */
  padding: 10px;
}

.vertical-bar a {
  color: #000; /* Ajusta el color de los enlaces según tus necesidades */
  text-decoration: none;
}

.vertical-bar a i {
  font-size: 20px; /* Ajusta el tamaño de los iconos según tus necesidades */
  margin-bottom: 10px; /* Ajusta el espaciado entre los iconos según tus necesidades */
}

/* A continuación, utiliza las clases "fa-icon1", "fa-icon2" y "fa-icon3" para definir los estilos de los iconos específicos */

.fa-icon1:before {
  content: "\f124"; /* Reemplaza XXX con el código correspondiente a tu primer icono */
}

.fa-icon2:before {
  content: "\f333"; /* Reemplaza XXX con el código correspondiente a tu segundo icono */
}

.fa-icon3:before {
  content: "\895"; /* Reemplaza XXX con el código correspondiente a tu tercer icono */
}
</style>
  