<template>
  <div class="container">
    <div v-for="cat in filteredPictosByCat" :key="cat.label" class="item">
      <h2 class="category-title">
        {{ cat.label }}
      </h2>

      <div class="picto-grid">
        <div v-for="picto in cat.pictos" :key="picto">
          <img :src="require(`~/assets/${picto}.png`)" alt="">
          <h3>{{ picto }}</h3>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'PictoGrid',

  props: {
    filteredPictosByCat: {
      type: Array,
      default: () => []
    }
  }
}
</script>

<style lang="scss" scoped>
.container {
  width: 80%;
  margin: 0 auto;
  max-width: 1200px;

  .category-title {
    font-size: 18px;
    font-weight: 600;
    color: #162a48;
    margin: 48px 0 40px;
  }

  .picto-grid {
    display: flex;
    flex-wrap: wrap;
    justify-content: flex-start;
    gap: 30px 60px;

    div {

      width: calc(25% - 60px);
      max-width: 150px;
      min-width: 80px;
      cursor: pointer;
      padding: 10px 20px;
      box-sizing:border-box;
      border-radius: 3px;
      transition-duration: 0.3s;
      min-height: 110px;

      img {
        width: 100%;
      }

      h3 {
        text-align: center;
        text-transform: capitalize;
        font-size: 0.9rem;
        margin-top: 10px;
      }

      &:hover {
        background: rgb(240, 248, 250);

        h3 {
          color: rgb(35, 105, 210);
        }

        img {
          filter: invert(34%) sepia(29%) saturate(6478%) hue-rotate(207deg) brightness(89%) contrast(83%);
        }
      }
    }

  }
}
</style>
