<template>
    <div v-if="data2" class="flex bg-slate-400 w-[60vh] h-36 p-4 m-4 justify-around rounded border border-black"> 
      <div 
        v-if="data2[0].characterDirection === 'Left'"
        class="w-28 h-28 bg-top bg-cover rounded-full bg-white"
        :style="{ backgroundImage: `url(${data2[0].image})` }"
      > 
      </div>
      <div class="grid max-w-[50%]">
        <h2 class="font-bold">{{ data2[0].character }}</h2>
        <p class="text-xs">{{ data2[0].quote }}</p>
      </div>
      <div 
        v-if="data2[0].characterDirection === 'Right'"
        class="w-28 h-28 bg-top bg-cover rounded-full bg-white"
        :style="{ backgroundImage: `url(${data2[0].image})` }"
      > 
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, onMounted } from 'vue';
  
  const data2 = ref(null);
  
  async function getData() {
    const response = await fetch('https://thesimpsonsquoteapi.glitch.me/quotes?count=1');
    const dataJSON = await response.json();
    console.log('API Response:', dataJSON);
    data2.value = dataJSON;
  }
  
  onMounted(() => {
    console.log('Component mounted');
    getData();
  });
  </script>
  
  <style scoped>
  .imagen {
    width: 100px;
    height: 100px;
    background-color: aqua;
    background-size: cover;
    background-position: center;
  }
  </style>
  