<script setup lang="ts">
import Header from '../components/Header.vue';
import Hero from '../components/Hero.vue';
import WhoWeAre from '../components/WhoWeAre.vue';
import Services from '../components/Services.vue';
import Data from '../components/Data.vue';
// import Blog from '../components/Blog.vue';
import Clients from '../components/Clients.vue';
import ContactUs from '../components/ContactUs.vue';
// import Testimonials from '../components/Testimonials.vue';
import Footer from '../components/Footer.vue';
</script>

<template>

<Header />
<main>

    <Hero />
    <WhoWeAre /> 
    <Services />
    <Data /> 
    <!-- <Blog /> -->
    <Clients />
    <ContactUs />
    <Footer />
    
</main>

</template>

<style scoped>
/* Styles from your original template, adapted to the new structure */
main{
    max-width: screen;
}
</style>
