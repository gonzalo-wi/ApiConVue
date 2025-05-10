<template>
  <div>
    <!-- Barra de navegación -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">Rick and Morty</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav">
            <li class="nav-item">
              <a class="nav-link active" aria-current="page" href="#">Home</a>
            </li>
          </ul>
        </div>
      </div>
    </nav>

    <!-- Contenido principal -->
    <div class="container mt-4">
      <h1 class="text-center">Personajes de Rick and Morty</h1>
      <div class="row">
        <div v-for="character in characters" :key="character.id" class="col-md-4 mb-4">
          <div class="card">
            <img :src="character.image" class="card-img-top" :alt="character.name" />
            <div class="card-body">
              <h5 class="card-title">{{ character.name }}</h5>
              <p class="card-text">Especie: {{ character.species }}</p>
              <p class="card-text">Estado: {{ character.status }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Footer -->
    <footer class="bg-dark text-white text-center py-3 mt-4">
      <p>&copy; 2025 Rick and Morty API Viewer</p>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'Characters',
  data() {
    return {
      characters: [],
    };
  },
  methods: {
    async fetchCharacters() {
      try {
        const response = await fetch('https://rickandmortyapi.com/api/character');
        const data = await response.json();
        this.characters = data.results;
      } catch (error) {
        console.error('Error fetching characters:', error);
      }
    },
  },
  mounted() {
    this.fetchCharacters();
  },
};
</script>

<style>
/* Puedes agregar estilos personalizados aquí */
</style>