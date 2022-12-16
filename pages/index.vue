<template>
  <div class="app-container">
    <Navbar />
    <Hero />
    <Search :filtered-pictos-by-cat="allPictosByCat" @input="updateQueryString" @select-category="selectCategory" />
    <PictoGrid :filtered-pictos-by-cat="filtered" />
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
import Navbar from '../components/AppNavbar.vue'
import Hero from '../components/AppHero.vue'
import Search from '../components/AppSearch.vue'
import PictoGrid from '../components/PictoGrid.vue'

export default Vue.extend({
  name: 'IndexPage',

  components: {
    Navbar,
    Hero,
    Search,
    PictoGrid
  },

  data () {
    return {

      allPictosByCat: [
        {
          label: 'Alimentaire',
          pictos: ['kiwi', 'citron', 'carotte', 'poisson', 'nourriture', 'milk-shake', 'salade']
        },
        {
          label: 'Sports',
          pictos: ['cycle', 'badminton', 'basketball', 'bowling', 'boxe', 'football', 'golf', 'ping-pong', 'rugby', 'tir-a-larc', 'volley']
        },
        {
          label: 'Animaux et végétaux',
          pictos: ['chien', 'insecte', 'oiseau', 'serpent', 'vache']
        },
        {
          label: 'Chiffres et lettres',
          pictos: ['1', '2', '3', '4', '5', '6', '7', '8', '9']
        },
        {
          label: 'Transport et véhicules',
          pictos: ['auto', 'avion', 'bus', 'camion', 'fusee', 'helicoptere', 'cycle']
        }
        // {
        //   label: 'Concepts',
        //   pictos: []
        // },
        // {
        //   label: 'Hygiène',
        //   pictos: []
        // },
        // {
        //   label: 'Action',
        //   pictos: []
        // },
        // {
        //   label: 'Activités',
        //   pictos: []
        // },
        // {
        //   label: 'Lieux',
        //   pictos: []
        // },
        // {
        //   label: 'Objets',
        //   pictos: []
        // },
        // {
        //   label: 'demandes',
        //   pictos: []
        // },
        // {
        //   label: 'Pays',
        //   pictos: []
        // },
        // {
        //   label: 'Famille',
        //   pictos: []
        // },
        // {
        //   label: 'Animaux',
        //   pictos: []
        // },
        // {
        //   label: 'Métiers',
        //   pictos: []
        // },
        // {
        //   label: 'Boissons',
        //   pictos: []
        // }
      ],
      queryString: '',
      selectedCategory: 'Tout'
    }
  },

  computed: {
    filtered () {
      return this.allPictosByCat.filter(cat => cat.label.toLowerCase().includes(this.queryString.toLowerCase()) || cat.pictos.some(picto => picto.toLowerCase().includes(this.queryString.toLowerCase()))).map((cat) => {
        // if category label corresponds
        if (cat.label.toLowerCase().includes(this.queryString.toLowerCase())) {
          return cat
        }
        // else if picto corresponds
        else if (cat.pictos.some(picto => picto.toLowerCase().includes(this.queryString.toLowerCase()))) {
          return { label: cat.label, pictos: [...cat.pictos.filter(picto => picto.toLowerCase().includes(this.queryString.toLowerCase()))] }
        }
      }).filter((cat) => {
        return this.selectedCategory === 'Tout' || this.selectedCategory === cat?.label
      })
    }
  },

  methods: {
    updateQueryString (newString: string) {
      this.queryString = newString
    },

    selectCategory (category) {
      this.selectedCategory = category
    }
  }
})
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Ubuntu&display=swap');

body,
html {
  padding: 0;
  margin: 0;
  font-family: 'Ubuntu', sans-serif;
}

* {
  transition: all 0.5s ease;
}

.app-container {
  position: relative;
}
</style>
