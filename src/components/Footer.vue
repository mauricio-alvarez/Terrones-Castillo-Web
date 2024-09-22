<template>
    <footer class="max-w-screen bg-black text-white py-12 px-4">
      <div class="max-w-7xl mx-auto">
        <!-- Logo -->
        <div class="mb-8">
          <img :src="logo" alt="Terrones & Castillo Logo" class="h-12 sm:h-16 w-auto max-h-16 filter invert" >
        </div>
  
        <!-- Main footer content -->
        <div class="grid grid-cols-1 md:grid-cols-4 gap-8">
          <!-- About Us -->
          <div>
            <h3 class="font-bold mb-4">About Us</h3>
            <ul class="space-y-2">
              <li><a href="#" class="hover:text-yellow-400">Our Results</a></li>
              <li><a href="#" class="hover:text-yellow-400">Who We Are</a></li>
              <li><a href="#" class="hover:text-yellow-400">In The Community</a></li>
              <li><a href="#" class="hover:text-yellow-400">Pound Law</a></li>
              <li><a href="#" class="hover:text-yellow-400">Referrals</a></li>
              <li><a href="#" class="hover:text-yellow-400">Careers | Join Our Team</a></li>
              <li><a href="#" class="hover:text-yellow-400">Shop</a></li>
              <li><a href="#" class="hover:text-yellow-400">Testimonials</a></li>
            </ul>
          </div>
  
          <!-- Resources -->
          <div>
            <h3 class="font-bold mb-4">Resources</h3>
            <ul class="space-y-2">
              <li><a href="#" class="hover:text-yellow-400">Blog</a></li>
              <li><a href="#" class="hover:text-yellow-400">Testimonials</a></li>
              <li><a href="#" class="hover:text-yellow-400">FAQ</a></li>
              <li><a href="#" class="hover:text-yellow-400">In The Media</a></li>
              <li><a href="#" class="hover:text-yellow-400">TV commercials</a></li>
              <li><a href="#" class="hover:text-yellow-400">Accessibility</a></li>
              <li><a href="#" class="hover:text-yellow-400">Complaints</a></li>
              <li><a href="#" class="hover:text-yellow-400">Opt Out</a></li>
              <li><a href="#" class="hover:text-yellow-400">Sitemap</a></li>
            </ul>
          </div>
  
          <!-- Quick Links -->
          <div>
            <h3 class="font-bold mb-4">Quick Links</h3>
            <ul class="space-y-2">
              <li><a href="#" class="hover:text-yellow-400">Car Accident Lawyer</a></li>
              <li><a href="#" class="hover:text-yellow-400">Slip and Fall Lawyer</a></li>
              <li><a href="#" class="hover:text-yellow-400">Truck Accident Lawyer</a></li>
              <li><a href="#" class="hover:text-yellow-400">Personal Injury Lawyer</a></li>
              <li><a href="#" class="hover:text-yellow-400">Labor and Employment Lawyer</a></li>
              <li><a href="#" class="hover:text-yellow-400">Medical Malpractice Lawyer</a></li>
              <li><a href="#" class="hover:text-yellow-400">Birth Injury Lawyer</a></li>
              <li><a href="#" class="hover:text-yellow-400">Brain Injury Lawyer</a></li>
            </ul>
          </div>
  
          <!-- Social -->
          <div>
            <h3 class="font-bold mb-4">Social</h3>
            <ul class="space-y-2">
              <li><a href="#" class="hover:text-yellow-400">X (Twitter)</a></li>
              <li><a href="#" class="hover:text-yellow-400">Facebook</a></li>
              <li><a href="#" class="hover:text-yellow-400">YouTube</a></li>
              <li><a href="#" class="hover:text-yellow-400">Instagram</a></li>
              <li><a href="#" class="hover:text-yellow-400">LinkedIn</a></li>
            </ul>
          </div>
        </div>
         
      <div class="container mx-auto pt-6 mb-6 mt-6 border-t border-gray-700 ">
        <!-- Footer Top Section: Address & Disclaimer -->
        <div class="flex flex-wrap justify-between items-start">
          <div class="w-full lg:w-2/3 text-xs mb-6 lg:mb-0">
            <p>20 North Orange Ave, Suite 1600, Orlando, FL 32801</p>
            <p>For a full list of locations in your area, please visit our Office Locations page.</p>
            <br />
            <p>This site is designed to be accessible to and usable by people with and without disabilities.
              Please contact us if you encounter an accessibility or usability issue on this site.
              Attorney advertising. Prior results do not guarantee a similar outcome.
            </p>
            <p class="mt-2">Your privacy choices.</p>
          </div>
        </div>
        
        <!-- Footer Bottom Section: Copyright & Links -->
        <div class="flex justify-between mt-6 items-center border-t border-gray-700 pt-4">
          <p class="text-xs">©2024 Terrones & Castillo, P.A. All rights reserved</p>
          <div class="text-xs space-x-4">
            <a href="/privacy-policy/" class="hover:underline">Privacy Policy</a>
            <a href="/disclaimer-and-terms-of-use/" class="hover:underline">Disclaimers and Terms of Use</a>
          </div>
        </div>
      </div>

      </div>
    </footer>
  </template>
  
  <script setup>
  import logo from '@/assets/LOGO TERRONES CASTILLO-cropped-cropped-bw.svg'

  </script>