<template>
  <Navbar :logo="logo_src" :alt="app_name" />
  <router-view/>
  <FooterVi/>
</template>

<script>
import Navbar from './components/Navbar.vue';
import FooterVi from './components/FooterVi.vue';

export default {
  components:{
    Navbar,
    FooterVi
  },
  data(){
    return {
      logo_src: "/img/logo.png",
      app_name: "Make Your Burguer"
    }
  }
}

</script>

<style >

*{
  font-family: Helvetica;
  padding: 0;
  margin: 0;
  box-sizing: border-box;
}

.main-container {
  margin: 50px;
  min-height: 250px;
}

h1 {
  text-align: center;
  font-size: 42px;
  margin-bottom: 30px;
  color: #222;
}
</style>
