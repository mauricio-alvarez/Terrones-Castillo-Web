<template>
    <section id="testimonials" class="max-w-screen">
      <h2>What Our Clients Say</h2>
      <div class="testimonials-grid">
        <div v-for="testimonial in testimonials" :key="testimonial.id" class="testimonial text-black">
          <p>"{{ testimonial.quote }}"</p>
          <span>- {{ testimonial.name }}</span>
        </div>
      </div>
    </section>
</template>
  
<script setup lang="ts">
  import { ref } from 'vue';
  
  // Define the structure of a testimonial
  interface Testimonial {
    id: number;
    name: string;
    quote: string;
  }
  
  // Define the array of testimonials
  const testimonials = ref<Testimonial[]>([
    { id: 1, name: 'John Doe', quote: 'Excellent legal advice and representation!' },
    { id: 2, name: 'Jane Smith', quote: 'Very professional and responsive.' },
  ]);
</script>


<style scoped>
  .testimonials-grid {
    display: grid;
    grid-template-columns: repeat(2, 1fr);
    gap: 20px;
  }
  .testimonial {
    background-color: #f9f9f9;
    padding: 20px;
    border-radius: 10px;
  }
  </style>
  