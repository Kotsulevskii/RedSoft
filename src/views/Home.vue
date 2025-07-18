<script setup lang="ts">
import { ref } from 'vue'
import Card from '../components/Card.vue'
import type { Product } from '../types/Product'

const products = ref<Product[]>([
  {
    id: 1,
    image: '/public/images/venera__born.png',
    title: '«Рождение Венеры»',
    author: 'Сандро Боттичелли',
    oldPrice: '2 000 000 $',
    price: '1 000 000 $',
  },
  {
    id: 2,
    image: '/public/images/last__supper.png',
    title: '«Тайная вечеря»',
    author: 'Леонардо да Винчи',
    oldPrice: undefined,
    price: '3 000 000 $',
  },
  {
    id: 3,
    image: '/public/images/create__adam.png ',
    title: '«Сотворение Адама»',
    author: 'Микеланджело',
    oldPrice: '6 000 000 $',
    price: '5 000 000 $',
  },
  {
    id: 4,
    image: '/public/images/anatomy__lesson.png',
    title: '«Урок анатомии»',
    author: 'Рембрандт',
    price: 'Продана на аукционе',
  },
])
</script>

<template>
    <section class="gallery">
      <h1 class="hero__title">Картины эпохи Возрождения</h1>
      <div class="container container--wrap container--gap-32">
        <Card v-for="product in products" :key="product.id" :product="product" />
      </div>
    </section>
</template>

<style scoped>

.gallery {
  display: flex;
  flex-direction: column;
  justify-content: center;
  max-width: 1200px;
  margin: 0 auto;
}

.hero__title {
  font-size: var(--font-title);
  line-height: 150%;
  font-weight: bold;
  color: var(--color-main);
  margin: 39px 0 45px 0;
  text-align: left;
}

@media (max-width: 1024px) {
  .container {
    justify-content: center;
  }
  .hero__title {
    text-align: center;
  }
}
</style>