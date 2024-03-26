<script setup>
import { RouterLink, RouterView } from 'vue-router'
</script>

<template>
  <header>
    <img
      alt="Vue logo"
      class="logo"
      src="@/assets/photo_2023-10-27_20-20-27.jpg"
      width="500"
      height="500"
    />

    <div class="wrapper">
      <nav>
        <RouterLink to="/">Главная страница</RouterLink>
        <RouterLink to="/todo">Todo-тест</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 300%;
  font-size: 54px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: green;
}

nav a.router-link-exact-active:hover {
  color: var(--color-text);
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
  color: var(--color-text);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    width: 100px;
    display: flex;
    place-items: flex-start;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}
</style>
