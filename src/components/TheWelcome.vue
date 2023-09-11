<script setup>

import axios from 'axios';
import {onMounted,ref} from 'vue'
const loading = ref(false);
const datas = ref([]);
onMounted(async()=>{
      try {
            loading.value = true;
            const res = await axios.get('https://api.github.com/users');
            const data = await res.data;
            datas.value = data;
        loading.value = false;
      } catch (error) {
        loading.value = false;
            console.log(error.message);
      }
})


</script>
<template>


<section class="text-gray-900 body-font">
  <div class="container px-5 py-24 mx-auto">
  
    <!-- {{ datas }} -->
    <div class="flex justify-center items-center">
      <v-icon v-if="datas.length<1 || loading" name="la-spinner-solid" class="text-3xl lg:text-6xl text-white animate-spin " scale="4"></v-icon>
    </div>
    <div v-if="datas.length>1" v-for="(data,index) in datas"  class="flex flex-wrap mb-14 -m-4">
      <div class="p-4 mx-auto duration-300 hover:scale-105 bg-white rounded-lg lg:w-1/2">
        <div class="h-full flex sm:flex-row flex-col items-center sm:justify-start justify-center text-center sm:text-left">
          <img alt="team" class="flex-shrink-0 rounded-lg w-48 h-48 object-cover sm:mb-0 mb-4" :src="data?.avatar_url">
          <div class="flex-grow sm:pl-8">
            <h2 class="title-font font-medium capitalize text-3xl text-gray-900">{{data?.login}}</h2>
            <p class="mb-4">
              Lorem ipsum, dolor sit amet consectetur adipisicing elit. Aspernatur fugiat dignissimos dolorem, dicta mollitia impedit quidem numquam.
            </p>
           <div class="flex  justify-center lg:justify-end mx-6">
            <a target="_blank" :href="data.html_url" class="inline-flex cursor-pointer text-white bg-indigo-500 border-0 py-2 px-6 focus:outline-none hover:bg-indigo-600 rounded text-lg">visit repo's</a>
           </div>
          
          </div>
        </div>
      </div>
    
    </div>
  </div>
</section>



</template>


<style lang="scss" scoped>

</style>