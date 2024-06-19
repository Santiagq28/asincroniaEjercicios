<script setup>
import { ref, onMounted } from 'vue';

const data = ref(null);
const isLoading = ref(true);

onMounted(async () => {
  try {
    const response = await fetch('/Ben10.json');
    data.value = await response.json();
  } catch (error) {
    console.error('Error al cargar el archivo JSON:', error);
  } finally {
    isLoading.value = false;
  }
});

const randomNumber = ref(0);
const generateRandomNumber = () => {
  randomNumber.value = Math.floor(Math.random() * 10) ; // Número aleatorio entre 1 y 100
};
onMounted(() => {
  generateRandomNumber();
});

//const data2 = ref(await fetch('/Ben10.json').then(res => res.json()))
</script>

<template>
 <div>
    <div v-if="isLoading">
      Loading...
    </div>
    <div v-else>
      <p>Nombre: {{ data.name }}</p>
      <p>Edad: {{ data.age }}</p>
      <p>AlienRandom: {{ data.aliens[randomNumber] }}</p>
    </div>
  </div>
</template>
