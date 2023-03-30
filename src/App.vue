<script setup lang="ts">
import {ref} from 'vue';
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import SlayLoader from '../lib/SlayLoader.vue'

const preloader = ref(false)
function changePreloader()  {
  preloader.value = !preloader.value;
}
</script>

<template>
  <SlayLoader
      :show="preloader"
      :animation="`fade`"
      :time="500"
      :background="`radial-gradient(circle, rgba(198,90,254,1) 0%, rgba(184,251,196,1) 100%)`"
      :spinner="`/assets/puff.svg`"
      :text="`Please wait, loading...`"
  />
  <button class="btn-change-preloader" @click="changePreloader">Change preloader</button>
  <header>
    <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />
    </div>
  </header>

  <main>
    <TheWelcome />
  </main>
</template>

<style scoped>
.btn-change-preloader {
  position: fixed;
  top: 20%;
  left: 20%;
  z-index: 9999;

}
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
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
}
</style>
