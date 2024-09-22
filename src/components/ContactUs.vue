<template>
    <div class="max-w-screen relative bg-cover bg-center bg-blue-900 text-white min-h-1/2 flex items-center justify-center p-4 "
    :style="{ backgroundImage: `url(${backgroundImage})` }">
    <!--    'bg-gradient-to-t from-black/50 to-black/20'  -->
    
    <!-- Dark overlay -->
    <div class="absolute inset-0 bg-black bg-opacity-55 z-0"></div>
    <!-- Content -->
      <div class="relative z-10 max-w-6xl w-full">
        
        <div class="grid md:grid-cols-2 gap-8 mb-8">
            
          <div>
            <h1 class="text-4xl font-bold mt-8 mb-2">CONTACTANOS</h1>
            <h2 class="text-3xl font-light mb-8">TERRONES & CASTILLO</h2>
            <div class="mb-8">
              <h3 class="text-xl font-semibold mb-2">NUESTRA DIRECCIÓN</h3>
              <p>Av. Los Rosales 122, 28021, Madrid.</p>
              <p>Email: info@misitio.com</p>
              <p>Tel: 914-123-456</p>
            </div>
            <a href="#" class="text-blue-300 hover:text-blue-100 transition-colors duration-300">
              Haz clic aquí para encontrarnos
            </a>
          </div>
          <div>
            <h2 class="text-3xl font-light mt-6 mb-8">CONTACTO</h2>
            <form @submit.prevent="handleSubmit" class="space-y-6">
              <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div class="group relative">
                  <label for="nombre" class="block w-full pb-1 text-sm font-medium text-gray-300 transition-all duration-200 ease-in-out group-focus-within:text-blue-300">Nombre</label>
                  <input 
                    v-model="form.nombre" 
                    type="text" 
                    id="nombre" 
                    required 
                    class="peer h-10 w-full rounded-md text-black bg-white bg-opacity-55 px-4 font-thin outline-none drop-shadow-sm transition-all duration-200 ease-in-out focus:bg-white focus:drop-shadow-lg"
                  />
                </div>
                <div class="group relative">
                  <label for="apellido" class="block w-full pb-1 text-sm font-medium text-gray-300 transition-all duration-200 ease-in-out group-focus-within:text-blue-300">Apellido</label>
                  <input 
                    v-model="form.apellido" 
                    type="text" 
                    id="apellido" 
                    required 
                    class="peer h-10 w-full rounded-md text-black bg-white bg-opacity-55 px-4 font-thin outline-none drop-shadow-sm transition-all duration-200 ease-in-out focus:bg-white focus:drop-shadow-lg"
                  />
                </div>
              </div>
              <div class="group relative">
                <label for="email" class="block w-full pb-1 text-sm font-medium text-gray-300 transition-all duration-200 ease-in-out group-focus-within:text-blue-300">Email *</label>
                <input 
                  v-model="form.email" 
                  type="email" 
                  id="email" 
                  required 
                  class="peer h-10 w-full rounded-md text-black bg-white bg-opacity-55 px-4 font-thin outline-none drop-shadow-sm transition-all duration-200 ease-in-out focus:bg-white focus:drop-shadow-lg"
                />
              </div>
              <div class="group relative">
                <label for="asunto" class="block w-full pb-1 text-sm font-medium text-gray-300 transition-all duration-200 ease-in-out group-focus-within:text-blue-300">Asunto</label>
                <input 
                  v-model="form.asunto" 
                  type="text" 
                  id="asunto" 
                  required 
                  class="peer h-10 w-full rounded-md text-black bg-white bg-opacity-55 px-4 font-thin outline-none drop-shadow-sm transition-all duration-200 ease-in-out focus:bg-white focus:drop-shadow-lg"
                />
              </div>
              <div class="group relative">
                <label for="mensaje" class="block w-full pb-1 text-sm font-medium text-gray-300 transition-all duration-200 ease-in-out group-focus-within:text-blue-300">Mensaje *</label>
                <textarea 
                  v-model="form.mensaje" 
                  id="mensaje" 
                  rows="3" 
                  required 
                  class="peer w-full rounded-md text-black bg-white bg-opacity-55 px-4 py-2 font-thin outline-none drop-shadow-sm transition-all duration-200 ease-in-out focus:bg-white focus:drop-shadow-lg resize-none"
                ></textarea>
              </div>
              <div class="text-right">
                <button 
                  type="submit" 
                  class="bg-white text-blue-900 px-8 py-2 rounded hover:bg-blue-100 transition-colors"
                >
                  Enviar
                </button>
              </div>
            </form>
          </div>
        </div>
        <!-- <div class="w-full">
          <iframe
            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3765.2700000000003!2d-99.1331!3d19.4326!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x0%3A0x0!2zMTnCsDI1JzU3LjQiTiA5OcKwMDcnNTkuMiJX!5e0!3m2!1sen!2sus!4v1620000000000!5m2!1sen!2sus"
            width="100%"
            height="400"
            style="border:0;"
            allowfullscreen=""
            loading="lazy"
          ></iframe>
        </div> -->
      </div>
    </div>
    
  </template>
  
  <script setup>
  import { reactive } from 'vue'
  
  const form = reactive({
    nombre: '',
    apellido: '',
    email: '',
    asunto: '',
    mensaje: ''
  })
  
  const handleSubmit = () => {
    // Here you would typically send the form data to a server
    console.log('Form submitted:', form)
    // Reset form after submission
    Object.keys(form).forEach(key => form[key] = '')
  }
  const backgroundImage = new URL('@/assets/lima-city.jpeg', import.meta.url).href

  </script>