<template>
  <div class="container">
    <Navigation/>
    <MyDescription/>
    <ProfessionnalExperience/>
    <Techno/>
    <Contact/>

  </div>
  
</template>

<script>
import Navigation from './components/NavBar.vue';
import MyDescription from './components/MyDescription.vue';
import ProfessionnalExperience from './components/ProfessionalExcperience.vue'
import Techno from './components/Techno.vue';
import Contact from './components/Contact.vue'


export default {
  name: 'App',
  components: {
    Navigation,
    MyDescription,
    ProfessionnalExperience,
    Techno,
    Contact


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
