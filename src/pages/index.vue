<template>
  <v-container>
    <h1 class="mb-6 text-center">Pokédex</h1>

    <v-row>
      <v-col
        v-for="pokemon in pokemons"
        :key="pokemon.id"
        cols="12"
        lg="3"
        md="4"
        sm="6"
      >
        <v-card class="mx-auto" max-width="300">
          <v-img
            :alt="`Image de ${pokemon.name}`"
            class="align-center"
            max-height="200"
            :src="`/images/${pokemon.img}`"
          />
          <v-card-title>{{ pokemon.name }}</v-card-title>
          <v-card-subtitle class="type-badges">
            <span
              v-for="type in pokemon.type.split(',')"
              :key="type"
              class="type-badge"
              :style="{ backgroundColor: obtenirLaCouleurDeFondDuType(type.trim()) }"
            >
              {{ type.trim() }}
            </span>
          </v-card-subtitle>
          <v-card-subtitle>Level: {{ pokemon.level }}</v-card-subtitle>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
  import { storeToRefs } from 'pinia'
  import { usePokemonStore } from '@/stores/pokemonStore'

  // Récupération du store Pokémon
  const pokemonStore = usePokemonStore()
  // Transformation des données réactives
  const { pokemons } = storeToRefs(pokemonStore)

  // Fonction pour déterminer la couleur de fond en fonction du type du Pokémon
  function obtenirLaCouleurDeFondDuType (type) {
    return pokemonStore.getTypeColor(type) || '#A8A878'
  }
</script>

<style scoped>
/* Styles pour les couleurs de fonds des types */
.type-badges {
  display: flex;
  gap: 8px;
  flex-wrap: wrap;
}

.type-badge {
  padding: 4px 8px;
  border-radius: 12px;
  color: white;
  font-weight: bold;
  font-size: 0.875em;
  text-align: center;
}
</style>
