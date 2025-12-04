<script setup>
import NavbarComponent from '@/components/nav/NavbarComponent.vue';
</script>
<template>
  <div class="min-h-screen bg-white dark:bg-gray-900 transition-colors duration-300">
    <header class="fixed top-0 w-full z-50 border-gray-100 dark:border-gray-800 bg-white/80 dark:bg-gray-900/80 backdrop-blur-sm">
      <NavbarComponent />
    </header>
    <main class="pt-20">
      <slot />
    </main>
  </div>
</template>
