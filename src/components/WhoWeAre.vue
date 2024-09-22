<template>
    <section class="max-w-screen bg-white py-16 px-4 sm:px-6 lg:px-8">
      <div class="max-w-7xl mx-auto">
        <div class="grid grid-cols-1 md:grid-cols-2 gap-8 items-center">
          <div class="relative h-64 md:h-96 overflow-hidden rounded-lg">
            <img
              :src="bg"
              alt="Modern office interior"
              class="w-full h-full object-cover"
            />
          </div>
          <div class="space-y-6">
            <h2 class="text-2xl font-semibold text-gray-900 uppercase tracking-wider">
              Nuestra Visión
            </h2>
            <blockquote class="text-3xl md:text-4xl font-light text-gray-900 leading-tight">
              Integridad y excelencia al servicio de nuestros clientes.              "
            </blockquote>
            <p class="text-lg text-gray-600">
              En Terrones & Castillo, nos esforzamos por ir más allá de los límites convencionales. 
              Nuestro compromiso es con la excelencia y la innovación continua en el campo legal.
              <!-- ser un estudio confiable y sostenible, brindando asesoría legal de calidad con integridad y compromiso hacia cada uno de nuestros clientes. -->
            </p>
          </div>
        </div>
      </div>
      <div class="max-w-7xl mx-auto mt-16">
        <hr class="border-t border-gray-200" />
      </div>
    </section>
  </template>
  
  <script setup>
  // No additional script needed for this component
  import bg from "@/assets/derecho-administrativo.jpg";
  </script>