<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import { ref } from 'vue'
import { useMessageStore } from '@/stores/message'
import { storeToRefs } from 'pinia'
const store = useMessageStore()
const { message } = storeToRefs(store)
const sizes = ref<number>(3)
</script>

<template>
  <header class="max-h-screen leading-normal">
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
      <nav>
        <RouterLink :to= "{name: 'event-list'}">Home</RouterLink>
        <RouterLink :to= "{name: 'about'}">About</RouterLink>
        <RouterLink :to= "{name: 'category'}">Category</RouterLink>
        <RouterLink :to= "{name: 'student'}">Student</RouterLink>
      </nav>
    </div>
  </header>
  <div class="size">
    <input type="number" class="sizes" min="1" v-model="sizes">
  </div>
  <div id="flashMessage" v-if="message"> 
        <h4>{{ message }}</h4>
      </div>

  <RouterView :size="sizes"/>
</template>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  /* width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem; */
  padding: 30px;
}

nav a.router-link-exact-active {
  /* color: var(--color-text); */
  color: #42b983;
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  /* display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border); */
  font-weight: bold;
  color:#2c3e50;
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
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
}

h4 {
  font-size: 20px;
}

@keyframes yellowfade {
  from {
    background: yellow;
  }
  to {
    background: transparent;
  }
}

#flashMessage {
  animation: yellowfade 3s ease-in-out;
}
.size {
  margin-left: 50%;
}

.sizes {
  width: 50px;
}
</style>
