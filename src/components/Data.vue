<template>
    <div class="max-w-screen relative min-h-[60vh] flex items-center justify-center p-4">
      <!-- Background Image with Filter -->
      <div
        class="absolute inset-0 bg-cover bg-center z-0"
        :style="{
          backgroundImage: 'url(' + backgroundImage + ')',
          filter: 'brightness(0.3) contrast(1.2)', /* Adjust the brightness and contrast */
        }"
      ></div>
  
      <!-- Dark Overlay -->
      <div class="absolute inset-0 bg-black bg-opacity-30 z-10"></div>
      
      <!-- Content (Statistics) -->
      <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8 z-20">
        <div v-for="(stat, index) in statistics" :key="index" class="text-center">
          <div class="text-4xl font-bold text-orange-500">
            <animated-number :value="stat.value" />
          </div>
          <div class="mt-2">{{ stat.label }}</div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  import AnimatedNumber from './AnimatedNumber.vue'
  
  // Import the image from the assets folder
  import backgroundImage from '../assets/bg-data.png'
  
  const statistics = ref([
    { value: 43, label: 'Clients' },
    { value: 68, label: 'Projects' },
    { value: 17, label: 'Awards' },
    { value: 12, label: 'Years Experience' },
  ])
  </script>
  