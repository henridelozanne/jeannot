<template>
  <div class="app-container">
    <Navbar />
    <Hero />
    <AppFooter />
  </div>
</template>

<script>
import Navbar from '../components/AppNavbar.vue'
import Hero from '../components/HomeHero2.vue'
import AppFooter from '../components/AppFooter.vue'

export default {
  name: 'Home2',

  components: {
    Navbar,
    Hero,
    AppFooter
  },

  data () {
    return {
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
          pictos: ['absent', 'empiler', 'autres', 'personne absente', 'retard']
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
          pictos: ['pluie']
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

  methods: {
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

<style>
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
}
</style>
