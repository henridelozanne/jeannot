<template>
  <div class="search">
    <select v-model="selectedCategory" @change="selectCategory">
      <option>
        Tout
      </option>
      <option v-for="category in filteredPictosByCat" :key="category.label">
        {{ category.label }}
      </option>
    </select>

    <div class="separator" />

    <div class="input-ctn">
      <SearchIcon />
      <input v-model="queryString" type="text" placeholder="Rechercher un pictogramme" @input="filterPictos">
    </div>
  </div>
</template>

<script>
import SearchIcon from '../components/SearchIcon.vue'

export default {
  name: 'AppSearch',

  components: { SearchIcon },

  props: {
    filteredPictosByCat: {
      type: Array,
      default: () => []
    }
  },

  data () {
    return {
      selectedCategory: 'Tout',
      queryString: ''
    }
  },

  methods: {
    filterPictos () {
      this.$emit('input', this.queryString)
    },

    selectCategory () {
      this.$emit('select-category', this.selectedCategory)
    }
  }
}
</script>

<style lang="scss" scoped>
.search {
  padding: 10px 16px;
  display: flex;
  align-items: center;
  position: sticky;
  width: 80%;
  max-width: 1200px;
  transform: translateY(-30px);
  border-radius: 2px;
  box-shadow: 0 3px 22px rgba(0, 0, 0, 0.1);
  background: white;
  margin: 0 auto;
  top: 30px;
  z-index: 2;

  select {
    width: 200px;
    height: 40px;
    border-radius: 2px;
    font-family: 'Ubuntu', sans-serif;
    padding: 0 10px;
    border: none;
    cursor: pointer;
    font-size: 16px;
    font-family: 'Ubuntu', sans-serif;
    font-weight: 200;
    color: #a3a3a3;

    &:focus {
      outline-width: 0;
    }
  }

  .separator {
    width: 1px;
    height: 40px;
    background: #a3a3a3;
    margin: 0 30px;
  }

  .input-ctn {
    display: flex;
    align-items: center;
    width: 100%;

    svg {
      width: 20px;
      height: 20px;
      fill: #a3a3a3;
      margin-right: 10px;
    }

    input {
      height: 40px;
      border: none;
      outline: none;
      width: 100%;
      font-size: 16px;
      font-family: 'Ubuntu', sans-serif;
      font-weight: 200;

      &::placeholder {
          font-weight: 200;
          font-size: 16px;
          color: #a3a3a3;
      }
    }
  }

}
</style>
