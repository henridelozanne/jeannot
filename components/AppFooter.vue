<template>
  <section>
    <div class="hero">
      <h1>AUTISM & ADVICE</h1>
      <ul>
        <li>
          <router-link to="/">
            Qui sommes-nous ?
          </router-link>
        </li>
        <li>
          <router-link to="auticto">
            Auticto
          </router-link>
        </li>
        <li><a target="_blank" href="mailto:autismnadvice@gmail.com”">Contact</a></li>
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
  background: white;
  box-shadow: 10px 0 10px rgba(205, 205, 205, 58%);

  .hero {
    margin: 0 auto;
    width: 80%;
    max-width: 1200px;
    padding: 70px 0;

    h1 {
      padding-left: 0;
      text-transform: uppercase;
      font-size: 1.2rem;
      letter-spacing: 2px;
      margin-bottom: 30px;
    }

    ul {
      list-style-type: none;
      padding-left: 0;

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
