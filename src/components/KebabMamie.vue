<!-- src/components/KebabDeMamie.vue -->
<template>
  <div class="kebab-page">
    <header class="hero">
      <h1>Kebab de Mamie</h1>
      <p>Le meilleur kebab fait maison, comme chez grand-ma !</p>
      <button class="btn-order">Commander maintenant</button>
    </header>

    <section class="menu">
      <h2>Notre Menu</h2>
      <ul class="menu-list">
        <li v-for="item in menu" :key="item.id" class="menu-item">
          <img :src="item.img" :alt="item.name" />
          <div class="info">
            <h3>{{ item.name }}</h3>
            <p>{{ item.desc }}</p>
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

<script setup>
import { reactive } from 'vue'

const menu = reactive([
  { id: 1, name: 'Classic Kebab', desc: 'Viande d’agneau, légumes frais, sauce blanche maison', price: 8.5, img: '/images/kebab1.jpg' },
  { id: 2, name: 'Kebab Poulet', desc: 'Poulet grillé, crudités croquantes, sauce moutarde douce', price: 8.0, img: '/images/kebab2.jpg' },
  { id: 3, name: 'Végé Kebab', desc: 'Falafels croustillants, houmous, salade, sauce citronnée', price: 7.5, img: '/images/kebab3.jpg' },
])
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
  font-family: 'Comfortaa', cursive;
  color: var(--text);
  background-color: var(--bg);
  min-height: 100vh;
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

.hero p {
  font-size: 1.2rem;
  margin-bottom: 1.5rem;
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
