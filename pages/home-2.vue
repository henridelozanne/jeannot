<template>
  <div class="app-container">
    <Navbar />
    <Hero />
    <AppFooter />
  </div>
</template>

<script>
import Navbar from '../components/AppNavbar.vue'
import Hero from '../components/HomeHero3.vue'
import AppFooter from '../components/AppFooter.vue'

export default {
  name: 'IndexPage',

  components: {
    Navbar,
    Hero,
    AppFooter
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Nunito+Sans:wght@200&family=Ubuntu:wght@400;500;700;&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Ubuntu&display=swap');

body,
html {
  padding: 0;
  margin: 0;
  font-family: 'Ubuntu', sans-serif;
}

* {
  transition: all 0.3s ease;
}

.app-container {
  position: relative;
}
</style>
