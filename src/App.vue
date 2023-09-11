<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import Navbar from './components/Navbar.vue';
</script>

<template>
        <div class="bg-gray-700 min-h-screen">
          <Navbar/>
  <RouterView />
        </div>
</template>

<style scoped>

</style>
