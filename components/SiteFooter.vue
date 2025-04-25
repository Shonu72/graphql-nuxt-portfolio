<script setup>
const links = [
  { name: 'GitHub', href: 'https://github.com', icon: 'entypo-social:github-with-circle' },
  { name: 'Twitter', href: 'https://twitter.com', icon: 'entypo-social:twitter' },
  { name: 'Facebook', href: 'https://facebook.com', icon: 'entypo-social:facebook' },
  { name: 'LinkedIn', href: 'https://www.linkedin.com', icon: 'entypo-social:linkedin-with-circle' },
  { name: 'Instagram', href: 'https://instagram.com', icon: 'entypo-social:instagram' }
]
</script>

<template>
  <footer class="bg-gray-800">
    <section class="mx-auto max-w-7xl px-4 py-6 sm:px-6 lg:px-8 text-gray-300 flex flex-col sm:flex-row items-center">
      <!-- Copyright text - centered on mobile, left-aligned on larger screens -->
      <p class="text-center sm:text-left mb-4 sm:mb-0 flex-1">
        HackerKernel&reg; 2025. &copy; All Rights Reserved
      </p>
      
      <!-- Social links - centered on all screens but takes less space on mobile -->
      <div class="flex flex-row justify-center gap-4 sm:gap-6">
        <a 
          v-for="link in links" 
          :key="link.name" 
          :href="link.href"
          :aria-label="link.name"
          class="hover:text-white transition-colors duration-200"
        >
          <Icon :name="link.icon" size="1.5rem" class="text-gray-300 hover:text-white" />
        </a>
      </div>
    </section>
  </footer>
</template>