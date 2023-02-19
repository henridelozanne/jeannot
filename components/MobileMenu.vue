<template>
  <ul class="mobile-menu">
    <li @click="closeMenu">
      <router-link to="/">
        Présentation
      </router-link>
    </li>

    <li @click="closeMenu">
      <router-link to="/auticto">
        Auticto
      </router-link>
    </li>

    <li @click="closeMenu">
      <a href="mailto:“adresse-mail-a-me-donner@gmail.com”">Contact</a>
    </li>
  </ul>
</template>

<script>
export default {
  name: 'MobileMenu',

  methods: {
    closeMenu () {
      this.$emit('toggle-mobile-menu', false)
    }
  }
}
</script>

<style lang="scss" scoped>
.mobile-menu {
  height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: column;
  list-style-type: none;
  padding-left: 0;
  margin-top: 0;
  font-size: 30px;
  margin-top: -97px;
  background-image: linear-gradient(to top, #dfe9f3 0%, white 100%);

  li:not(:last-of-type) {
    margin-bottom: 40px;
  }

  li a {
    color: rgb(64, 64, 64);
    text-decoration: none;
  }
}
</style>
