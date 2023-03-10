<template>
  <div class="app-container">
    <Navbar />
    <Hero />
    <Search :filtered-pictos-by-cat="allPictosByCat" @input="updateQueryString" @select-category="selectCategory" />
    <PictoGrid :filtered-pictos-by-cat="filtered" @open-modal="openModal" />
    <PictoModal v-if="modalVisible" :picto="currentPicto" @close-modal="modalVisible = false" />
    <AppFooter />

    <transition ransition name="fade" appear>
      <div v-if="scY > 300" id="pagetop" class="fixed right-0 bottom-0" @click="toTop">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          width="80"
          height="80"
          viewBox="0 0 24 24"
          fill="none"
          stroke="#4a5568"
          stroke-width="1"
          stroke-linecap="square"
          stroke-linejoin="arcs"
        >
          <path d="M18 15l-6-6-6 6" />
        </svg>
      </div>
    </transition>
  </div>
</template>

<script>
import _ from 'lodash'
import Navbar from '../components/AppNavbar.vue'
import Hero from '../components/AutictoHero.vue'
import Search from '../components/AppSearch.vue'
import PictoGrid from '../components/PictoGrid.vue'
import PictoModal from '../components/PictoModal.vue'
import AppFooter from '../components/AppFooter.vue'

export default {
  name: 'IndexPage',

  components: {
    Navbar,
    Hero,
    Search,
    PictoGrid,
    PictoModal,
    AppFooter
  },

  data () {
    return {
      scTimer: 0,
      scY: 0,
      allPictosByCat: [
        {
          label: 'Actions',
          pictos: ['boire', 'dessiner', 'ecrire', 'faire des bulles', 'jouer', 'lire', 'manger', 'raconter une histoire']
        },
        {
          label: 'Activités',
          pictos: ['activité théâtre', 'arts plastiques', 'classe', 'courses', 'danse', 'équithérapie', 'jardinage', 'jouer', 'musique', 'pause', 'piscine', 'promenade', 'psychomotricité', 'regroupement', 'sport', 'travailler']
        },
        {
          label: 'Alimentaire',
          pictos: ['ananas', 'banane', 'bonbon', 'bouteille', "broc d'eau", 'carotte', 'céréales', 'chips', 'compote', 'confiture', 'couteau', 'cuillère', 'cuisiner', 'eau', 'fourchette', 'fromage', 'gâteau', 'goûter', 'miel', 'nesquik', 'nutella', 'pain', 'petit-déjeuner', 'pomme', 'raisin', 'repas', 'tisane', 'yahourt']
        },
        {
          label: 'Animaux',
          pictos: ['chat', 'chien', 'coccinelle', 'oiseau', 'papillon', 'poisson', 'vache']
        },
        {
          label: 'Chiffres et lettres',
          pictos: ['0', '1', '2', '3', '4', '5', '6', '7', '8', '9', 'A', 'B', 'C', 'D', 'E', 'F', 'G', 'H', 'I', 'J', 'L', 'M', 'N', 'O', 'P', 'Q', 'R', 'S', 'T', 'U', 'V', 'W', 'X', 'Y', 'Z']
        },
        {
          label: 'Concept',
          pictos: ['empiler', 'retard']
        },
        {
          label: 'Repères spatiaux',
          pictos: ['à côté', "à l'intérieur", 'derrière', 'dessous', 'dessus', 'devant', 'entre']
        },
        {
          label: 'Écran',
          pictos: ['ordinateur', 'tablette', 'télévision', 'téléphone']
        },
        {
          label: 'Formes de base',
          pictos: ['coeur', 'étoile', 'triangle']
        },
        {
          label: 'Hygiène',
          pictos: ['brosse à dents', 'douche', 'laver les mains', 'prendre le bain', 'toilettes']
        },
        {
          label: 'Lieux',
          pictos: ['au travail', 'cour haut', 'cour des petits', 'cour du bas', 'école', 'hôpital', 'infirmerie', 'maison', 'récréation', 'salle de consultation', 'salle de retour au calme', 'salle polyvalente']
        },
        {
          label: 'Matières scolaires',
          pictos: ['anglais', 'date', 'mathématiques', 'poésie']
        },
        {
          label: 'Médical',
          pictos: ['gel hydroalcoolique', 'masque chirurgical', 'pansement']
        },
        {
          label: 'Objets',
          pictos: ['ballon de baudruche', 'ballon', 'bulle', 'cartes', 'chaise', 'ciseaux', 'clé', 'crayon', 'cube', 'emploi du temps', 'fleur', 'gomme', 'grande poubelle', 'lego', 'porte-manteau vide', 'porte-manteau', 'poubelle', 'puzzle', 'raquette', 'sablier', 'sac à dos', 'scotch', 'table', 'tasse', 'tipi', 'trampoline', 'trotinette', 'trousse', 'vélo']
        },
        {
          label: 'Sensoriel',
          pictos: ['mains sur la tête', 'pression pied']
        },
        {
          label: 'Temps',
          pictos: ['soleil', 'pluie', 'neige', 'nuage']
        },
        {
          label: 'Transport et véhicules',
          pictos: ['ambulance', 'bus', 'camion', 'hélicoptère', 'metro indisponible', 'metro', 'metro signe', 'taxi', 'train', 'train 2', 'tramway indisponible', 'tramway signe', 'tramway', 'voiture', 'voiture indisponible']
        },
        {
          label: 'Vestimentaire',
          pictos: ['bonnet', 'casquette', 'chaussure', 'chemise', 'couche', 'enlever la couche', 'pantalon', 'pull', 'slip culotte', 't-shirt']
        }
      ],
      currentPicto: '',
      queryString: '',
      selectedCategory: 'Tout',
      modalVisible: false
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

  mounted () {
    window.addEventListener('scroll', this.handleScroll)
  },

  methods: {
    conditionGoTop () {
      this.scTimer = setTimeout(() => {
        this.scY = window.scrollY
        clearTimeout(this.scTimer)
        this.scTimer = 0
      })
    },

    handleScroll: _.debounce(function () {
      this.conditionGoTop()
    }, 300),

    toTop () {
      window.scrollTo({
        top: 0,
        behavior: 'smooth'
      })
    },

    openModal (picto) {
      this.currentPicto = picto
      this.modalVisible = true
    },

    updateQueryString (newString) {
      this.queryString = newString
    },

    selectCategory (category) {
      this.selectedCategory = category
    }
  }
}
</script>

<style lang="scss">
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

#pagetop {
  position: fixed;
  opacity: 0.7;
  bottom: 20px;
  right: 20px;
  border-radius: 50%;
  width: 80px;
  height: 80px;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;

  &:hover {
      opacity: 0.5
  }
}
</style>
