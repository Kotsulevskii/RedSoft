<script setup lang="ts">
import { ref } from 'vue'
import type { Product } from '../types/Product'

const props = defineProps<{
  product: Product
}>()

const loading = ref(false)
const inCart = ref(checkInCart())
const imageLoaded = ref(false)

function checkInCart(): boolean {
  const cart = localStorage.getItem('cart')
  if (!cart) return false
  const ids = JSON.parse(cart) as number[]
  return ids.includes(props.product.id)
}

async function addToCart() {
  loading.value = true
  try {
    const res = await fetch('https://jsonplaceholder.typicode.com/posts/1 ')
    if (res.ok) {
      inCart.value = true
      saveToLocalStorage()
     
    }
  } catch (err) {
    console.error(err)
  } finally {
    loading.value = false
  }
}

async function removeFromCart() {
  loading.value = true
  try {
    const res = await fetch('https://jsonplaceholder.typicode.com/posts/1 ')
    if (res.ok) {
      inCart.value = false
      removeFromLocalStorage()
     
    }
  } catch (err) {
    console.error(err)
  } finally {
    loading.value = false
  }
}

function saveToLocalStorage() {
  const cartItems = JSON.parse(localStorage.getItem('cart') || '[]') as number[]
  if (!cartItems.includes(props.product.id)) {
    cartItems.push(props.product.id)
    localStorage.setItem('cart', JSON.stringify(cartItems))
  }
}

function removeFromLocalStorage() {
  const cartItems = JSON.parse(localStorage.getItem('cart') || '[]') as number[]
  const updatedItems = cartItems.filter(id => id !== props.product.id)
  localStorage.setItem('cart', JSON.stringify(updatedItems))
}
</script>

<template>
  <div
    class="card"
    :class="{ 'card--sold': product.price === 'Продана на аукционе' }"
  >
    <div v-if="!imageLoaded" class="card__image-placeholder"></div>
    <img
      v-show="imageLoaded"
      :src="product.image"
      :alt="product.title"
      class="card__image"
      @load="imageLoaded = true"
    />
    <div class="card__content">
      <h2 class="card__content--text">{{ product.title }} 
        <p class="card__content--text">{{ product.author }}</p>
      </h2>
      <div class="card__active">
        <div class="card__price">
          <p v-if="product.oldPrice" class="card__old-price">{{ product.oldPrice }}</p>
          <p class="card__new-price">{{ product.price }}</p>
        </div>
        <button
          v-if="!inCart && product.price !== 'Продана на аукционе'"
          @click="addToCart"
          class="button card__button"
          :class="{ 'card__button--loading': loading }"
        >
          {{ loading ? 'Загрузка...' : 'Купить' }}
        </button>
        <button 
          v-else-if="inCart && product.price !== 'Продана на аукционе'" 
          class="button button--alt card__button card__button--in-cart"
           @click="removeFromCart"
        >
          <div class="card__button--check">
            <div class="check-icon"></div><div>В корзине</div>
          </div>
        </button>
      </div>
    </div>
  </div>
</template>

<style scoped>
.card {
  border: var(--border-main);
  overflow: hidden;
  background-color: var(--bg-card);
}
.card--sold {
  opacity: 0.5;
}
.card__image {
  width: 100%;
  height: 200px;
  object-fit: cover;
}
.card__image-placeholder {
  width: 350px;
  height: 200px;
  background-color: var(--bg-placeholder);
}
.card__content {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  padding: 24px;
  height: 200px;
  text-align: left;
}
.card__content--text {
  font-size: var(--font-card-title);
  font-weight: 400;
  line-height: 150%;
  color: var(--color-main);
  margin: 0;
}
.card__active {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-top: 22px;
}
.card__price {
  display: flex;
  flex-direction: column;
}
.card__old-price {
  margin: 0;
  text-decoration: line-through;
  font-size: var(--font-main);
  font-weight: 300;
  color: var(--color-muted);
}
.card__new-price {
  font-size: var(--font-large);
  color: var(--color-main);
  font-weight: bold; 
  margin: 0;
}
.card__button {
  width: 135px;
}
.card__button--in-cart {
  padding: 14px 8px;
}
.card__button--check {
  display: flex;
  align-items: center;
  gap: 5px;
}
.check-icon {
  width: 20px;
  height: 20px;
  background-image: url('../assets/feather_check.png');
  background-position: center;
  background-repeat: no-repeat;
  background-size: contain;
}
</style>
