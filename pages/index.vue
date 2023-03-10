<template>
  <div class="app-container">
    <Navbar :mobile-menu-is-opened="mobileMenuIsOpened" class="navbar" @toggle-mobile-menu="toggleMobileMenu" />

    <div v-if="!mobileMenuIsOpened" class="main-content">
      <Hero />
      <AppFooter />
    </div>

    <MobileMenu v-else @toggle-mobile-menu="toggleMobileMenu" />
  </div>
</template>

<script>
import Navbar from '../components/AppNavbar.vue'
import Hero from '../components/HomeHero.vue'
import AppFooter from '../components/AppFooter.vue'

export default {
  name: 'IndexPage',

  components: {
    Navbar,
    Hero,
    AppFooter
  },

  data () {
    return {
      mobileMenuIsOpened: false
    }
  },

  methods: {
    toggleMobileMenu (value) {
      this.mobileMenuIsOpened = value
    }
  }
}
</script>

<style lang="scss">
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

  .main-content {
    margin-top: 50px;
  }
}

.navbar {
  position: fixed;
  top: 0;
  width: 100%;
  background: transparent;
  z-index: 1;
}
</style>
