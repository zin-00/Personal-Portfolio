<script setup>
import { onMounted, ref } from 'vue'
import { animate, stagger } from 'animejs'

const logoRef = ref(null)
const navLinksRef = ref(null)
const darkModeButtonRef = ref(null)
const isDark = ref(false)

const toggleDarkMode = () => {
  isDark.value = !isDark.value
  document.documentElement.classList.toggle('dark', isDark.value)
  localStorage.setItem('darkMode', isDark.value ? 'dark' : 'light')
}

const smoothScroll = (e, targetId) => {
  e.preventDefault()
  const target = document.querySelector(targetId)
  if (target) {
    target.scrollIntoView({
      behavior: 'smooth',
      block: 'start'
    })
  }
}

onMounted(() => {
  // Check for saved preference or system preference
  const savedTheme = localStorage.getItem('darkMode')
  if (savedTheme === 'dark' || (!savedTheme && window.matchMedia('(prefers-color-scheme: dark)').matches)) {
    isDark.value = true
    document.documentElement.classList.add('dark')
  }

  // Animate the logo
  animate(logoRef.value, {
    translateX: [-50, 0],
    opacity: [0, 1],
    duration: 800,
    ease: 'easeOutExpo'
  })

  // Animate the nav links with stagger
  animate(navLinksRef.value.children, {
    translateY: [-20, 0],
    opacity: [0, 1],
    duration: 600,
    delay: stagger(100, { start: 300 }),
    ease: 'easeOutExpo'
  })

  // Animate the dark mode button
  animate(darkModeButtonRef.value, {
    translateY: [-20, 0],
    opacity: [0, 1],
    duration: 600,
    delay: 700,
    ease: 'easeOutExpo'
  })
})
</script>
<template>
  <nav class="max-w-6xl mx-auto px-6 py-6">
    <div class="flex items-center justify-between">
      <!-- Left Side - Name/Logo -->
      <a
        ref="logoRef"
        href="#home"
        @click="(e) => smoothScroll(e, '#home')"
        class="text-lg font-medium opacity-0 text-black dark:text-white hover:opacity-70 transition-opacity"
      >
        M.
      </a>

      <!-- Right Side - Nav Links -->
      <div class="flex items-center">
        <div ref="navLinksRef" class="hidden md:flex items-center gap-8">
          <a
            href="#projects"
            @click="(e) => smoothScroll(e, '#projects')"
            class="text-sm text-gray-500 hover:text-black dark:hover:text-white opacity-0 transition-colors"
          >
            Projects
          </a>
          <a
            href="#tech-stacks"
            @click="(e) => smoothScroll(e, '#tech-stacks')"
            class="text-sm text-gray-500 hover:text-black dark:hover:text-white opacity-0 transition-colors"
          >
            Skills
          </a>
          <a
            href="#certificates"
            @click="(e) => smoothScroll(e, '#certificates')"
            class="text-sm text-gray-500 hover:text-black dark:hover:text-white opacity-0 transition-colors"
          >
            Certificates
          </a>
          <a
            href="#contacts"
            @click="(e) => smoothScroll(e, '#contacts')"
            class="text-sm text-gray-500 hover:text-black dark:hover:text-white opacity-0 transition-colors"
          >
            Contact
          </a>
        </div>
        <button
          ref="darkModeButtonRef"
          @click="toggleDarkMode"
          class="ml-8 text-gray-400 hover:text-black dark:hover:text-white transition-colors opacity-0"
          aria-label="Toggle dark mode"
        >
          <!-- Sun icon -->
          <svg v-if="isDark" xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M12 3v1m0 16v1m9-9h-1M4 12H3m15.364 6.364l-.707-.707M6.343 6.343l-.707-.707m12.728 0l-.707.707M6.343 17.657l-.707.707M16 12a4 4 0 11-8 0 4 4 0 018 0z" />
          </svg>
          <!-- Moon icon -->
          <svg v-else xmlns="http://www.w3.org/2000/svg" class="h-5 w-5" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M20.354 15.354A9 9 0 018.646 3.646 9.003 9.003 0 0012 21a9.003 9.003 0 008.354-5.646z" />
          </svg>
        </button>
      </div>
    </div>
  </nav>
</template>
