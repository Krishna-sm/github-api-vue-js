<template>
  <header class="text-white bg-gray-900 body-font">
  <div class="container mx-auto flex flex-wrap p-5 flex-col md:flex-row items-center">
    <RouterLink to="/" class="flex title-font font-medium items-center  mb-4 md:mb-0">
    
      <span class="ml-3 text-xl">Github</span>
    </RouterLink>
    <nav class="md:ml-auto flex flex-wrap items-center text-base justify-center">
      <RouterLink to="/" class="mr-5 duration-300 hover:text-black hover:px-12 hover:py-2 hover:bg-white hover:rounded-md">Home</RouterLink>
      <RouterLink to="/search" class="mr-5 duration-300 hover:text-black hover:px-12 hover:py-2 hover:bg-white hover:rounded-md">Search</RouterLink>
    </nav>
    
  </div>
</header>
</template>

<script setup>
import {RouterLink} from 'vue-router'
</script>

<style lang="scss" scoped>

</style>