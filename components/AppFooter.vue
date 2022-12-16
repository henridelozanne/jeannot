<template>
  <section>
    <div class="hero">
      <h1>Auticto</h1>
      <ul>
        <li><a href="">Qui sommes-nous ?</a></li>
        <li><a href="">Contact</a></li>
        <li><a href="">Mentions légales</a></li>
      </ul>
    </div>
  </section>
</template>

<script>
export default {
  name: 'AppFooter'
}
</script>

<style lang="scss" scoped>
section {
  background-image: radial-gradient( circle farthest-corner at 10% 20%,  rgba(234,249,249,0.67) 0.1%, rgba(239,249,251,0.63) 90.1% );
  margin-top: 60px;

  .hero {
    margin: 0 auto;
    width: 80%;
    max-width: 1200px;
    // text-align: right;
    padding: 70px 0;

    h1 {
      padding-left: 40px;
      text-transform: uppercase;
      font-size: 1.2rem;
      letter-spacing: 2px;
      margin-bottom: 30px;
    }

    ul {
      list-style-type: none;

      li:not(:first-of-type) {
        margin-top: 12px;
      }

      a {
        text-decoration: none;
        color: rgb(39, 39, 39);
      }
    }
  }

  @media screen and (max-width: 700px) {
    .hero {
      padding-bottom: 100px;
    }
  }

}
</style>
