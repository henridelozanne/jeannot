<template>
  <section>
    <div class="hero">
      <h1>La banque de pictogrammes adaptés aux personnes autistes</h1>
      <h4>Lorem ipsum dolor sit amet consectetur, adipisicing elit. Debitis quidem possimus iure officiis corrupti ipsum itaque, veritatis nesciunt? Corrupti blanditiis doloremque incidunt modi! Dolorum, hic quos? Harum aliquid eum id.</h4>
    </div>
  </section>
</template>

<script>
export default {
  name: 'AppHero'
}
</script>

<style lang="scss" scoped>
section {
  background-image: radial-gradient( circle farthest-corner at 10% 20%,  rgba(234,249,249,0.67) 0.1%, rgba(239,249,251,0.63) 90.1% );

  .hero {
    margin: 0 auto;
    width: 80%;
    max-width: 1200px;
    text-align: center;
    padding: 70px 0;

    h1 {
      font-size: 24px;
      font-weight: 600;
      color: #162a48;
    }

    h4 {
      font-size: 16px;
      font-weight: 400;
      line-height: 2;
      color: #646668;
      margin: 0 auto;
    }
  }

}
</style>
