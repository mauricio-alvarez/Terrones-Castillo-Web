<template>
  <nav :class="[
    ' max-w-screen fixed top-0 left-0 right-0 z-50 transition-colors duration-300',
    isTransparent ? 'bg-transparent' : 'bg-white shadow-md',
    isMenuOpen ? 'bg-white shadow-md': 'bg-transparent'  
  ]">
    <div class="max-w-screen max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <div class="flex items-center justify-between h-28">
      <div class="flex items-center">
        <a href="#" class="flex items-center">
          <img :src="logo" alt="Terrones & Castillo Logo" class="h-18 sm:h-18 w-auto max-h-20" :class="isMenuOpen ? '': [isTransparent ? 'filter invert' : '']  ">
        </a>
        </div>
        <div class="hidden lg:block">
          <div class="ml-10 flex items-baseline space-x-4">
            <a v-for="item in menuItems" :key="item" :href="'#' + item.toLowerCase()" 
               :class="[
                 'px-3 py-2 rounded-md text-xl font-medium',
                 isTransparent ? 'text-gray-300 hover:text-white' : 'text-gray-700 hover:text-gray-900'
               ]">
              {{ item }}
            </a>
          </div>
        </div>
        <div class="lg:hidden">
          <button @click="toggleMenu" :class="[
            'inline-flex items-center justify-center p-2 rounded-md',
            isMenuOpen ? 'text-gray-700 hover:text-gray-900':
            [isTransparent ? 'text-gray-300 hover:text-white' : 'text-gray-700 hover:text-gray-900']
          ]">
            <svg class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
              <path v-if="!isMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16" />
              <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12" />
            </svg>
          </button>
        </div>
      </div>
    </div>
    <transition
      enter-active-class="transition ease-out duration-100 transform"
      enter-from-class="opacity-0 scale-95"
      enter-to-class="opacity-100 scale-100"
      leave-active-class="transition ease-in duration-75 transform"
      leave-from-class="opacity-100 scale-100"
      leave-to-class="opacity-0 scale-95"
    >
      <div v-if="isMenuOpen" class="lg:hidden">
        <div class="px-2 pt-2 pb-3 space-y-1 sm:px-3">
          <a v-for="item in menuItems" :key="item" :href="'#' + item.toLowerCase()"
             :class="[
               'block px-3 py-2 rounded-md text-base font-medium',
               
               isMenuOpen ? 'text-gray-700 hover:text-gray-900':
               [isTransparent ? 'text-gray-300 hover:text-white' : 'text-gray-700 hover:text-gray-900']
             ]">
            {{ item }}
          </a>
        </div>
      </div>
    </transition>
  </nav>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import logo from '@/assets/LOGO TERRONES CASTILLO-cropped-cropped-bw.svg'

const isTransparent = ref(true)
const isMenuOpen = ref(false)
const menuItems = ['EXPERTISE', 'PEOPLE', 'INSIGHTS', 'LOCATIONS', 'CAREERS']

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const checkTransparency = () => {
  const heroSection = document.querySelector('.hero')
  if (heroSection) {
    const heroBottom = heroSection.getBoundingClientRect().bottom
    isTransparent.value = heroBottom > 0
  }
}

onMounted(() => {
  window.addEventListener('scroll', checkTransparency)
  checkTransparency() // Initial check
})

onUnmounted(() => {
  window.removeEventListener('scroll', checkTransparency)
})
</script>