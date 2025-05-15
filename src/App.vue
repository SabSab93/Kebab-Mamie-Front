<template>
  <div id="app">
    <!-- Header avec tes logos -->
    <header class="header-logos">
      <a href="https://vite.dev" target="_blank">
        <img src="/vite.svg" class="logo" alt="Vite logo" />
      </a>
      <a href="https://vuejs.org/" target="_blank">
        <img src="./assets/vue.svg" class="logo vue" alt="Vue logo" />
      </a>
    </header>

    <!-- Ici, la page Kebab de Mamie -->
    <KebabMamie />
  </div>
</template>

<style scoped>
/* Logos */
.header-logos {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 1rem;
}
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
  transition: filter 300ms;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>

<script setup lang="ts">
import KebabMamie from './components/KebabMamie.vue'
</script>
