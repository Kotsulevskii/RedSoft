<script setup lang="ts">
  import { ref } from 'vue'

  const menuOpen = ref(false)

  function toggleMenu() {
    menuOpen.value = !menuOpen.value
  }

  const searchQuery = ref('')

  const clearSearch = () => {
    searchQuery.value = ''
  }
</script>

<template>
  <header class="header">
    <div class="container">
      <div class="header__logo">
        <img src="../assets/logo.png" alt="Logo" />
      </div>
      <nav class="header__menu" :class="{ open: menuOpen }">
        <ul>
          <li><a href="#">Каталог</a></li>
          <li><a href="#">Доставка</a></li>
          <li><a href="#">Оплата</a></li>
          <li><a href="#">Контакты</a></li>
          <li><a href="#">О галерее</a></li>
        </ul>
      </nav>
       <div class="header__burger" @click="toggleMenu" :class="{ open: menuOpen }">
        <span></span>
        <span></span>
        <span></span>
      </div>
      <form class="header__search">
        <div class="search-input-wrapper">
          <input
            type="text"
            v-model="searchQuery"
            placeholder="Поиск по названию картины"
          />
          <button
            v-if="searchQuery"
            type="button"
            class="clear-button"
            @click="clearSearch"
          >
            ✕
          </button>
        </div>
        <button type="submit" class="button button--header">Найти</button>
      </form>
    </div>
  </header>
</template>

<style scoped>
.header {
  background-color: var(--bg-main);
  border-bottom: var(--border-main);
  padding: 24px 10px;
  position: sticky;
  top: 0;
  z-index: 10;
}
.container {
  max-width: 1200px;
  margin: 0 auto;
  display: flex;
  justify-content: space-between;
  align-items: center;
  position: relative;
}
.header__logo img {
  width: 50px;
}
.header__menu ul {
  padding: 0;
  list-style: none;
  display: flex;
  gap: 48px;
}
.header__menu li a {
  font-size: var(--font-main);
  text-decoration: none;
  color: var(--color-main);
}
.header__search input {
  box-sizing: border-box;
  padding: 14px 60px 14px 16px;
  border: var(--border-main);
  background-color: var(--bg-app);
  font-family: Merriweather, serif;
  font-size: var(--font-main);
}

.search-input-wrapper {
  position: relative;
  display: inline-block;
}

.clear-button {
  position: absolute;
  right: 8px;
  top: 50%;
  transform: translateY(-50%);
  background: none;
  border: none;
  cursor: pointer;
  font-size: 16px;
  color: #999;
}

.header__burger {
  display: none;
  width: 36px;
  height: 36px;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  cursor: pointer;
  z-index: 3;
}
.header__burger span {
  display: block;
  width: 28px;
  height: 4px;
  margin: 4px 0;
  background: #343030;
  border-radius: 2px;
  transition: 0.3s;
}
.header__burger.open span:nth-child(1) {
  transform: translateY(12px) rotate(45deg);
}
.header__burger.open span:nth-child(2) {
  opacity: 0;
}
.header__burger.open span:nth-child(3) {
  transform: translateY(-12px) rotate(-45deg);
}


@media (max-width: 1024px) {
  .header__menu ul {
    gap: 24px;
  }
  .header__menu li a,
  .header__search input,
  .header__search button {
    font-size: 14px;
  }
  .header__search input,
  .header__search button {
    padding: 14px;
  }
}

@media (max-width: 705px) {
  .container {
    flex-wrap: wrap;
    flex-direction: row;
    align-items: flex-start;
  }
  .header__burger {
    display: flex;
    margin-left: 16px;
  }
  .header__menu {
    position: absolute;
    top: 65px;
    left: 0;
    width: 100%;
    background: #ECEAEA;
    box-shadow: 0 2px 8px rgba(0,0,0,0.04);
    transform: translateY(-200%);
    transition: transform 0.5s;
    z-index: 3;
    padding: 24px 0 16px 0;
    display: block;
  }
  .header__menu.open {
    transform: translateY(0);
  }
  .header__menu ul {
    flex-direction: column;
    gap: 18px;
    align-items: flex-start;
    margin: 0 24px;
  }
  .header__menu li a {
    font-size: 24px;
  }
  .header__search {
    width: 100%;
    margin-top: 12px;
    text-align: center;
    order: 3;
  }
  .header__logo {
    order: 1;
  }
  .header__burger {
    order: 2;
  }
  .header__menu {
    order: 4;
  }
}
</style>