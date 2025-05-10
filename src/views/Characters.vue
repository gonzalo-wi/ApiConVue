<template>
  <div>
    <!-- Navbar -->
    <nav class="navbar navbar-expand-lg navbar-dark bg-dark shadow-sm">
      <div class="container">
        <a class="navbar-brand fw-bold" href="#">Rick and Morty</a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav ms-auto">
            <li class="nav-item">
              <a class="nav-link active" href="#">Inicio</a>
            </li>
          </ul>
        </div>
      </div>
    </nav>

    <!-- Contenido -->
    <div class="container mt-5">
      <h1 class="text-center mb-4">🌌 Personajes de Rick and Morty</h1>
      <div class="row">
        <div
          v-for="character in characters"
          :key="character.id"
          class="col-sm-6 col-md-4 mb-4"
        >
          <div class="card h-100 shadow-sm rounded-4 hover-card">
            <img
              :src="character.image"
              class="card-img-top rounded-top-4"
              :alt="character.name"
            />
            <div class="card-body text-center">
              <h5 class="card-title fw-semibold">{{ character.name }}</h5>
              <p class="card-text mb-1">🧬 Especie: {{ character.species }}</p>
              <p class="card-text">💀 Estado: {{ character.status }}</p>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!-- Footer -->
    <footer class="bg-dark text-white text-center py-3 mt-5 shadow-sm">
      <p class="mb-0">&copy; 2025 Rick and Morty API Viewer - Gonza Dev</p>
    </footer>
  </div>
</template>

<script>
export default {
  name: "Characters",
  data() {
    return {
      characters: [],
    };
  },
  methods: {
    async fetchCharacters() {
      try {
        const res = await fetch("https://rickandmortyapi.com/api/character");
        const data = await res.json();
        this.characters = data.results;
      } catch (error) {
        console.error("Error fetching characters:", error);
      }
    },
  },
  mounted() {
    this.fetchCharacters();
  },
};
</script>

<style>
.hover-card {
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}
.hover-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 20px rgba(0, 0, 0, 0.15);
}
</style>