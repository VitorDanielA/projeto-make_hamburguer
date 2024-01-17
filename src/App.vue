<template>
  <div>
    <NavBar/>
    <router-view/>
    <Footer/>
  </div>
</template>

<script>

  import NavBar from './views/NavBar.vue';
  import Footer from './views/Footer.vue';

  export default {
    name: 'App',
    components: {
      NavBar,
      Footer
    }
  }
</script>

<style>
  *{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
    font-family: Helvetica;
  }
</style>