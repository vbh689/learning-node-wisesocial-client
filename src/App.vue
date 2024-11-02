<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import DemoComponent from './components/DemoComponent.vue';

</script>

<template>
  <header>
    <div class="wrapper">
      <nav>
        <!-- <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/base">Parent Component</RouterLink> -->
      </nav>
    </div>
  </header>

  <!-- <RouterView /> -->
</template>

<script>
export default {
  methods: {
    clickMe() {
      alert(0);
    }
  }
}
</script>

<style scoped>

</style>
