<template>
    <div class="max-w-screen bg-white py-12 px-4 sm:px-6 lg:px-8">
      <div class="max-w-7xl mx-auto">
        <h2 class="text-3xl font-extrabold text-black text-center mb-8">
          {{ title }}
        </h2>
        <div class="border border-gray-500 overflow-hidden">
          <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4">
            <div 
              v-for="(client, index) in clients" 
              :key="client.name" 
              class="col-span-1 flex justify-center items-center p-12 border-gray-500"
              :class="{
                'border-b': index < clients.length - (clients.length % 2 || 2),
                'border-r': (index + 1) % 2 !== 0,
                'md:border-r': (index + 1) % 3 !== 0,
                'lg:border-r': (index + 1) % 4 !== 0,
                'md:border-b': index < clients.length - (clients.length % 3 || 3),
                'lg:border-b': index < clients.length - (clients.length % 4 || 4)
              }"
            >
              <img
                :src="client.logo"
                :alt="client.name"
                class="max-h-20 max-w-full object-contain"
              />
            </div>
          </div>
        </div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue'
  
  const title = ref('NUESTROS CLIENTES')
  
  const clients = ref([
    { name: 'KENO', logo: new URL('@/assets/Chambers-2024.jpg',import.meta.url ).href},
    { name: 'lendo', logo: new URL('@/assets/Leading-Lights.jpg',import.meta.url ).href },
    { name: 'DMG', logo: new URL('@/assets/logo-hys.svg',import.meta.url ).href},
    { name: 'Athos', logo: new URL('@/assets/iflr1000.png',import.meta.url ).href},
    // Add more clients as needed
  ])

  
  </script>