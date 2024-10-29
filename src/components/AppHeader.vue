<template>
  <v-app-bar flat>
    <v-container class="d-flex align-start align-center">
      <v-avatar
        class="mr-4 pa-0 cursor-pointer"
        image="@/assets/pokeball.svg"
        size="64"
        @click="$router.push('/')"
      />
      <v-toolbar-title>Pokedex</v-toolbar-title>
      <v-btn
        v-for="link in menuItems"
        :key="link.title"
        :icon="link.icon"
        :to="link.path"
      />
    </v-container>
  </v-app-bar>
</template>

<script setup>
  import { reactive } from 'vue'

  const menuItems = reactive([
    { title: 'Accueil', path: '/', icon: 'mdi-pokeball' },
    { title: 'Mes Pokemons Favoris', path: '/MesPokemonsFavoris', icon: 'mdi-heart' },
    { title: 'FAQ', path: '/FoireAuxQuestions', icon: 'mdi-comment-multiple' },
    { title: 'Monde', path: '/LeMondePokemon', icon: 'mdi-map' },
  ])
</script>
