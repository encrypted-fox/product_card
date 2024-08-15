<template>
  <div>
    <ProductCard :product="product"></ProductCard>
  </div>
</template>

<script setup>
import ProductCard from "./components/ProductCard.vue"

const product = {
  sizesArray: [
    { id: 1, value: 40 },
    { id: 2, value: 41 },
    { id: 3, value: 42 },
    { id: 4, value: 43 },
    { id: 5, value: 44 },
    { id: 6, value: 45 },
    { id: 7, value: 46 },
  ],

  initialSize: 4,

  colorsArray: [
    { id: 1, color: "#4B80CE" },
    { id: 2, color: "#5DCE4B" },
    { id: 3, color: "#F2962A" },
    { id: 4, color: "#F26F97" },
    { id: 5, color: "#F00048" },
  ],

  initialColor: 1,

  rating: 4,
  price: '1.500 ₽',

  name: 'AIRSOFT SNEAKERS',
  slogan: 'Представляем новую коллекцию!',
  category: 'СПОРТИВНАЯ ХОДЬБА',
  top: 'ТОП',
  isNew: true,

  logoLink: `url(${require('./assets/sneakers-logo.svg')})`,
  imageLink: `url(${require('./assets/sneakers-image.png')})`

}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:ital,opsz,wght@0,14..32,100..900;1,14..32,100..900&display=swap');

#app {
  font-family: 'Inter', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
