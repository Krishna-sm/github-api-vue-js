    
    <script setup>
    import axios from 'axios';
import {ref} from 'vue';

    const inputData = ref('');
    const loading = ref(false);
    const datas = ref(null);
    const fetchedData = async()=>{
        try {
            loading.value = true;
            const res = await axios.get(`https://api.github.com/users/${inputData.value}`);
            const data = await res.data;
            datas.value = data;
        loading.value = false;
      } catch (error) {
        loading.value = false;
            console.log(error.message);
      }
    }

    </script>
<template>
   <div class="flex justify-center flex-col items-center">
    
               <form @submit.prevent="fetchedData" class="my-10 w-1/2 mx-auto bg-white flex items-center px-3 rounded-md">
                <input v-model="inputData" type="text" placeholder="Search Any User" class="w-full h-10 py-10 text-gray-900 px-3 focus:outline-none focus:border-none text-2xl rounded-md ">
               <button type="submit" >
                <v-icon name="pr-search" scale="2" class="text-red-600" />
               </button>
               </form>
   
               <v-icon v-if="loading" name="la-spinner-solid" class="text-3xl lg:text-6xl text-white animate-spin " scale="4"></v-icon>

            <section v-if="datas || inputData.length>1" class="text-black mx-10 my-5 bg-white body-font">
  <div class="container mx-auto flex   md:flex-row flex-col items-center">
    <div class="lg:max-w-lg lg:w-full  md:w-1/2 w-5/6 mb-10 md:mb-0">
      <img class="  scale-110 object-cover object-center rounded-[3rem]" alt="hero" :src="datas?.avatar_url">
    </div>
    <div class="lg:flex-grow md:w-1/2 lg:pl-24 md:pl-16 flex flex-col md:items-start md:text-left items-center text-center">
      <h1 class="title-font sm:text-4xl text-3xl mb-4 font-medium text-gray-900">{{datas?.login}}
      </h1>
      <p class="mb-8 leading-relaxed">{{ datas?.bio??'Copper mug try-hard pitchfork pour-over freegan heirloom neutra air plant cold-pressed tacos poke beard tote bag. Heirloom echo park mlkshk tote bag selvage hot chicken authentic tumeric truffaut hexagon try-hard chambray.' }}</p>
      <div class="flex justify-center">
        <a :href="datas?.html_url" class="inline-flex text-white bg-indigo-500 border-0 py-2 px-6 focus:outline-none hover:bg-indigo-600 rounded text-lg">Visit Repo's</a>
        
      </div>
    </div>
  </div>
</section>

   </div>
</template>

<style lang="scss" scoped>

</style>