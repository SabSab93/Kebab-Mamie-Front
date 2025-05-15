
<template>
  <div class="kebab-page">
    <header class="hero">
      <h1>Kebab de Mamie</h1>
      <p v-if="error" class="error">{{ error }}</p>
      <p v-else-if="loading">Chargement…</p>
      <button v-else class="btn-order">Commander maintenant</button>
    </header>

    <section class="menu" v-if="!loading && !error">
      <h2>Notre Menu</h2>
      <ul class="menu-list">
        <li v-for="item in menu" :key="item.id" class="menu-item">
          <img :src="item.img" :alt="item.name" />
          <div class="info">
            <h3>{{ item.name }}</h3>
            <p>{{ item.description }}</p>
            <span class="price">{{ item.price }} €</span>
          </div>
        </li>
      </ul>
    </section>

    <footer class="footer">
      <p>📍 12 rue du Petit Marché, 75001 Paris • 📞 01 23 45 67 89</p>
    </footer>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

interface Kebab {
  id: number
  name: string
  description: string
  price: number
  img: string
}

const menu = ref<Kebab[]>([])
const loading = ref(true)
const error = ref<string | null>(null)

// URL de ton API Render
const API_URL = 'https://kebab-mamie.onrender.com/'


onMounted(async () => {
  console.log('Fetch →', API_URL)
  try {
    const res = await fetch(API_URL)
    console.log('Status:', res.status)
    if (!res.ok) throw new Error(`Erreur ${res.status}`)
    menu.value = await res.json()
  } catch (e) {
    console.error(e)
    error.value = (e as Error).message
  } finally {
    loading.value = false
  }
})
</script>

<style scoped>
/* Import d’une typo conviviale */
@import url('https://fonts.googleapis.com/css2?family=Comfortaa:wght@400;700&display=swap');

:root {
  --primary: #d1175b;    /* rose profond */
  --secondary: #f5a623;  /* jaune chaud */
  --bg: #111;            /* fond sombre */
  --text: #eee;
  --btn-glow: rgba(209,23,91,0.6);
}

.kebab-page {
  width: 100%;
  flex: 1;
  display: flex;
  flex-direction: column;
}

.hero {
  text-align: center;
  padding: 4rem 1rem;
  background: linear-gradient(135deg, var(--primary), var(--secondary));
  box-shadow: 0 0 20px var(--btn-glow);
}

.hero h1 {
  font-size: 3rem;
  margin-bottom: 0.5rem;
}

.error {
  color: #f55;
  margin-bottom: 1rem;
}

.btn-order {
  background: var(--bg);
  color: var(--secondary);
  border: 2px solid var(--text);
  padding: 0.75rem 1.5rem;
  font-size: 1rem;
  cursor: pointer;
  box-shadow: 0 0 10px var(--btn-glow);
  transition: transform 0.2s, box-shadow 0.2s;
}

.btn-order:hover {
  transform: scale(1.05);
  box-shadow: 0 0 20px var(--btn-glow);
}

.menu {
  flex: 1;
  padding: 2rem 1rem;
}

.menu h2 {
  text-align: center;
  margin-bottom: 1.5rem;
  font-size: 2rem;
  color: var(--secondary);
}

.menu-list {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1.5rem;
}

.menu-item {
  background: #222;
  border-radius: 1rem;
  overflow: hidden;
  box-shadow: 0 2px 8px rgba(0,0,0,0.5);
  display: flex;
  flex-direction: column;
  align-items: center;
}

.menu-item img {
  width: 100%;
  height: 160px;
  object-fit: cover;
}

.menu-item .info {
  padding: 1rem;
  text-align: center;
}

.menu-item h3 {
  margin: 0.5rem 0;
  font-size: 1.25rem;
}

.price {
  display: block;
  margin-top: 0.5rem;
  font-weight: bold;
  color: var(--primary);
}

.footer {
  text-align: center;
  padding: 1rem;
  background: #000;
  font-size: 0.9rem;
}
</style>
