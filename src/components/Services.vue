<template>
  <section class="max-w-screen bg-neutral-300 py-16">
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
      <h2 class="text-4xl font-bold text-gray-900 mb-8 font-playfair">Áreas de Especialización</h2>
      
      <div class="relative overflow-hidden" ref="carouselContainer" @touchstart="touchStart" @touchmove="touchMove" @touchend="touchEnd">
        <div class="flex transition-transform duration-300 ease-in-out" :style="{ transform: `translateX(-${currentSlide * (100 / itemsPerSlide)}%)` }">
          <div v-for="(topic, index) in topics" :key="index" :class="[
            'flex-shrink-0 transition-all duration-300 ease-in-out px-2',
            {
              'w-full': itemsPerSlide === 1,
              'w-1/2': itemsPerSlide === 2,
              'w-1/3': itemsPerSlide === 3
            }
          ]">
            <div class="relative h-80 rounded-lg overflow-hidden shadow-lg" :style="{
              backgroundImage: `url(${getImageUrl(topic.image)})`,
              backgroundSize: 'cover',
              backgroundPosition: 'center',
            }">
              <div class="absolute top-0 left-0 right-0 bg-opacity-80 p-4" :class="topic.color">
                <h3 class="text-xl font-bold text-white font-playfair">
                  <a href="/" class="hover:underline">
                    {{ topic.title }}
                  </a>
                </h3>
              </div>
            </div>
          </div>
        </div>
      </div>
      
      <div class="mt-8 flex justify-center items-center space-x-4">
        <button @click="prevSlide" class="p-2 rounded-full bg-white text-gray-600 hover:bg-gray-300 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-400 transition-colors duration-200">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7"></path>
          </svg>
        </button>
        <div class="flex space-x-2">
          <button 
            v-for="index in Math.ceil(topics.length / itemsPerSlide)" 
            :key="index" 
            @click="goToSlide((index - 1) * itemsPerSlide)"
            :class="[
              'w-3 h-3 rounded-full transition-colors duration-200',
              isActiveDot(index) ? 'bg-blue-600' : 'bg-white'
            ]"
          ></button>
        </div>
        <button @click="nextSlide" class="p-2 rounded-full bg-white text-gray-600 hover:bg-gray-300 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-gray-400 transition-colors duration-200">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7"></path>
          </svg>
        </button>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed, onMounted, onUnmounted } from 'vue'

const currentSlide = ref(0)
const itemsPerSlide = ref(3)
const touchStartX = ref(0)
const touchEndX = ref(0)
// lighter blue: bg-slate-700 / bg-sky-950
// dark blue: bg-slate-900
// grey: bg-slate-600
const topics = ref([
  { title: 'Derecho Administrativo', image: 'derecho-administrativo', color: 'bg-slate-900' },
  { title: 'Protección al Consumidor', image: 'derecho-administrativo', color: 'bg-slate-700 ' },
  { title: 'Contrataciones con el Estado', color: 'bg-slate-600', image: 'derecho-administrativo' },
  { title: 'Derecho Administrativo Sancionador', image: 'derecho-administrativo', color: 'bg-slate-900' },
  { title: 'Regulación de Servicios Públicos', image: 'derecho-administrativo', color: 'bg-slate-700' },
  { title: 'Derecho Administrativo Disciplinario', image: 'derecho-administrativo', color: 'bg-slate-600' },
  { title: 'Derecho Constitucional', image: 'derecho-administrativo', color: 'bg-slate-900' },
  { title: 'Derecho Procesal Constitucional', image: 'derecho-administrativo', color: 'bg-slate-700' },
  { title: 'Derecho Penal', image: 'derecho-administrativo', color: 'bg-slate-600' },
  { title: 'Derecho Laboral', image: 'derecho-administrativo', color: 'bg-slate-900' },
  { title: 'Derecho Civil', image: 'derecho-administrativo', color: 'bg-sky-950' }
])

const nextSlide = () => {
  currentSlide.value = (currentSlide.value + itemsPerSlide.value) % topics.value.length
}

const prevSlide = () => {
  currentSlide.value = (currentSlide.value - itemsPerSlide.value + topics.value.length) % topics.value.length
}

const goToSlide = (index) => {
  currentSlide.value = index
}

const handleResize = () => {
  const width = window.innerWidth
  if (width < 640) {
    itemsPerSlide.value = 1
  } else if (width < 1024) {
    itemsPerSlide.value = 2
  } else {
    itemsPerSlide.value = 3
  }
  currentSlide.value = Math.min(currentSlide.value, topics.value.length - itemsPerSlide.value)
}

const touchStart = (e) => {
  touchStartX.value = e.changedTouches[0].screenX
}

const touchMove = (e) => {
  touchEndX.value = e.changedTouches[0].screenX
}

const touchEnd = () => {
  const difference = touchStartX.value - touchEndX.value
  const threshold = 50 // minimum distance to be considered a swipe
  if (difference > threshold) {
    nextSlide()
  } else if (difference < -threshold) {
    prevSlide()
  }
}

const getImageUrl = (name) => {
  return new URL(`../assets/${name}.jpg`, import.meta.url).href
}

const isActiveDot = computed(() => (index) => {
  const start = Math.floor(currentSlide.value / itemsPerSlide.value)
  return index - 1 === start
})

onMounted(() => {
  handleResize()
  window.addEventListener('resize', handleResize)
})

onUnmounted(() => {
  window.removeEventListener('resize', handleResize)
})
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Playfair+Display:wght@400;700&display=swap');

.font-playfair {
  font-family: 'Playfair Display', serif;
}
</style>