<template>
  <div class="sidebar">
    <ul>
      <li v-for="item in menuItems" :key="item">
        {{ item }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  setup () {
    const menuItems = [
      'Accueil',
      'Alimentaire',
      'Animaux et végétaux',
      'Chiffres et lettres',
      'Concepts',
      'Hygiène',
      'Action',
      'Activités',
      'Lieux',
      'Objets',
      'Transport et véhicules',
      'demandes',
      'Sports',
      'Pays',
      'Famille',
      'Animaux',
      'Métiers',
      'Boissons',
      'Livres'
    ]

    return { menuItems }
  }
}
</script>

<style>
.sidebar {
  background: black;
  color: white;
  width: 200px;
  max-height: 100vh;
  padding: 40px 20px;
  overflow-y: scroll;
  text-align: center;
}

.sidebar ul {
  font-size: 1.5rem;
  list-style-type: none;
  margin: 0;
  padding: 0;
}

.sidebar ul li:not(:first-of-type) {
  margin-top: 20px;
}
</style>
