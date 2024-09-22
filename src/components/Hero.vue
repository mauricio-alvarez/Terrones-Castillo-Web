  <template>
    <section class="max-w-screen hero relative w-screen h-screen  flex items-center justify-center overflow-hidden bg-navy-blue ">
      <!-- Background Video -->
      <video
        autoplay
        loop
        muted
        class="absolute inset-0 w-full h-full object-cover opacity-20 max-w-screen"
        :poster="fallbackImage"
      >
        <source :src="videoSource" type="video/mp4" />
        Your browser does not support the video tag.
      </video>
  
      <!-- Content Overlay -->
      <div class="z-20 relative text-left max-w-4xl mx-auto px-4 max-w-screen">
        <h2 class="text-4xl sm:text-5xl md:text-6xl font-bold mb-4 text-teal-400 max-w-screen">
          Artificial Intelligence
        </h2>
        <h1 class="text-3xl sm:text-4xl md:text-5xl font-bold mb-6 text-white max-w-screen">
          Killer apps meet global law
        </h1>
        <p class="text-lg sm:text-xl text-gray-300 mb-8 max-w-2xl">
          As investment pours into AI, businesses strive for use cases and regulators rethink rulebooks, our resource hub pulls together our latest thinking for clients
        </p>
        <a
          href="#"
          class="inline-flex items-center text-white hover:text-teal-400 transition duration-300 max-w-screen"
        >
          Learn More
          <svg class="w-5 h-5 ml-2" fill="none" stroke="currentColor" viewBox="0 0 24 24" xmlns="http://www.w3.org/2000/svg">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M17 8l4 4m0 0l-4 4m4-4H3"></path>
          </svg>
        </a>
      </div>
    </section>
  </template>
  
  <script>
  export default {
    name: 'Hero',
    props: {
      videoSource: {
        type: String,
        default: 'https://res-2.cloudinary.com/fieldfisher/video/upload/so_auto/f_auto,q_auto/europe_homepage_video_final_webm_tnhxqg.webm'
      },
      fallbackImage: {
        type: String,
        default: 'https://images.unsplash.com/photo-1498092651296-641e88c3b057'
      }
    }
  }
  </script>
  
  <style scoped>
  .bg-navy-blue {
    background-color: #001f3f;
  }
  .text-teal-400 {
    color: #4fd1c5;
  }
  </style>
