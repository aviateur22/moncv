<template>
  <Navigation/>
</template>

<script>
import Navigation from './components/NavBar.vue'


export default {
  name: 'App',
  components: {
    Navigation
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:ital,wght@0,100;0,300;0,400;0,500;0,700;0,900;1,100;1,300;1,400;1,500;1,700;1,900&display=swap');

html, body {
  font-family: 'Roboto', sans-serif;
}
#app {
  font-family: 'Roboto', sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

}
</style>
