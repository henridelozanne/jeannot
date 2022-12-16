<template>
  <nav>
    <h1 class="website-title">
      <ImagesIcon />
      Auticto
    </h1>
  </nav>
</template>

<script>
import ImagesIcon from './ImagesIcon.vue'

export default {
  name: 'AppNavbar',

  components: { ImagesIcon }
}
</script>

<style lang="scss">
nav {
  padding: 20px 30px 20px 40px;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.15);
  position: relative;

  .website-title {
    cursor: pointer;
    text-transform: uppercase;
    margin: 0;
    font-size: 1.2rem;
    text-underline-offset: 3px;
    transition: all 1s ease;
    font-weight: 700;
    font-size: 1rem;
    letter-spacing: 4px;
    display: flex;
    align-items: center;

    svg {
      width: 30px;
      margin-right: 10px;
    }

    &:hover {
      color: rgb(20, 98, 77);

      svg {
        fill: rgb(20, 98, 77);
        transform: rotate(-10deg);
      }

    }
  }
}
</style>
