# RedSoft

Веб-приложение на Vue 3 + TypeScript для тествого задания фирмы RedSoft.

## Стек технологий
- [Vue 3](https://vuejs.org/)
- [TypeScript](https://www.typescriptlang.org/)
- [Vite](https://vitejs.dev/) — быстрый сборщик
- [vue-router](https://router.vuejs.org/) — маршрутизация

## Быстрый старт

### 1. Клонирование репозитория
```bash
# Клонируйте репозиторий и перейдите в папку проекта
 git clone <repo-url>
 cd RedSoft
```

### 2. Установка зависимостей
```bash
npm install
```

### 3. Запуск в режиме разработки
```bash
npm run dev
```

Приложение будет доступно по адресу, который выведет Vite (обычно http://localhost:5173).

### 4. Сборка для продакшена
```bash
npm run build
```

### 5. Предпросмотр production-сборки
```bash
npm run preview
```

## Структура проекта
```
RedSoft/
  src/
    components/   # Vue-компоненты (Header, Footer, Card и др.)
    views/        # Страницы (Home.vue)
    assets/       # Локальные изображения и иконки
    router/       # Маршрутизация
    types/        # Типы TypeScript
    style.css     # Глобальные стили и переменные
  public/         # Публичные изображения
  index.html      # Точка входа
  package.json    # Скрипты и зависимости
```

## Особенности
- Используются CSS-переменные для цветов, размеров шрифтов и других повторяющихся свойств.
- Глобальные утилитарные классы для контейнеров и кнопок.
- Мобильная адаптация для Header и Footer.
- Корзина реализована через localStorage (демо-режим).

