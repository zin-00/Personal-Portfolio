<script setup>
import GuestLayout from '@/layouts/GuestLayout.vue';
import { onMounted, ref, onUnmounted } from 'vue';
import { animate, stagger } from 'animejs';
import MeImage from '@/assets/images/Me.png';
import {
  BsGit,
  FaBandsGithubAlt,
  DeJavascriptOriginal,
  DeVuejsOriginal,
  CoBrandPhp,
  DeLaravelOriginal,
  DeJavaOriginalWordmark,
  DePythonOriginalWordmark,
  DeVitejsOriginal,
  DeTailwindcssOriginal,
  CoBrandLinux,
  CaEmail,
  DeLinkedinOriginal,
  BsTwitterX,
  DeVscodeOriginal,
  DeVisualstudioPlain,
  DeCsharpOriginal,
} from '@kalimahapps/vue-icons';

const heroContentRef = ref(null);
const imageRef = ref(null);
const techStacksRef = ref(null);
const contactsRef = ref(null);
const projectsRef = ref(null);
const certificatesRef = ref(null);
let observer = null;

const technologies = [
  { name: 'Git', icon: BsGit },
  { name: 'GitHub', icon: FaBandsGithubAlt },
  { name: 'JavaScript', icon: DeJavascriptOriginal },
  { name: 'Vue.js', icon: DeVuejsOriginal },
  { name: 'Vite', icon: DeVitejsOriginal },
  { name: 'Tailwind', icon: DeTailwindcssOriginal },
  { name: 'PHP', icon: CoBrandPhp },
  { name: 'Laravel', icon: DeLaravelOriginal },
  { name: 'Java', icon: DeJavaOriginalWordmark },
  { name: 'Python', icon: DePythonOriginalWordmark },
  { name: 'C#', icon: DeCsharpOriginal },
  { name: 'VS Code', icon: DeVscodeOriginal },
  { name: 'Visual Studio', icon: DeVisualstudioPlain },
  { name: 'Linux', icon: CoBrandLinux },
];

const certificates = [
  { name: 'Mobile App Development', issuer: 'Certificate of Completion', year: '2024' },
  { name: 'Smart Contract Training', issuer: 'Blockchain Development', year: '2024' },
];

const socialLinks = [
  { icon: FaBandsGithubAlt, label: 'GitHub', href: 'https://github.com/zin-00' },
  { icon: DeLinkedinOriginal, label: 'LinkedIn', href: 'https://www.linkedin.com/in/meljun-mariquit-1294b7342' },
  { icon: BsTwitterX, label: 'Twitter', href: 'https://https://x.com/zinblck' },
  { icon: CaEmail, label: 'Email', href: 'mailto:meljun.mariquit26@gmail.com' },
];

const setupScrollAnimations = () => {
  observer = new IntersectionObserver((entries) => {
    entries.forEach((entry) => {
      if (entry.isIntersecting) {
        const target = entry.target;

        if (target === contactsRef.value) {
          animate(target.querySelectorAll('.animate-item'), {
            opacity: [0, 1],
            translateY: [20, 0],
            delay: stagger(80),
            duration: 600,
            ease: 'easeOutExpo'
          });
        }

        if (target === projectsRef.value) {
          animate(target.querySelectorAll('.animate-item'), {
            opacity: [0, 1],
            translateY: [20, 0],
            delay: stagger(80),
            duration: 600,
            ease: 'easeOutExpo'
          });
        }

        if (target === techStacksRef.value) {
          animate('.tech-card', {
            opacity: [0, 1],
            scale: [0.9, 1],
            delay: stagger(40),
            duration: 500,
            ease: 'easeOutExpo'
          });
        }

        if (target === certificatesRef.value) {
          animate(target.querySelectorAll('.cert-card'), {
            opacity: [0, 1],
            translateY: [20, 0],
            delay: stagger(100),
            duration: 600,
            ease: 'easeOutExpo'
          });
        }

        observer.unobserve(target);
      }
    });
  }, { threshold: 0.1 });

  if (contactsRef.value) observer.observe(contactsRef.value);
  if (projectsRef.value) observer.observe(projectsRef.value);
  if (techStacksRef.value) observer.observe(techStacksRef.value);
  if (certificatesRef.value) observer.observe(certificatesRef.value);
};

const sendEmail = () => {
  window.location.href = 'mailto:your.email@example.com';
};

const downloadCV = () => {
  window.open('/cv.pdf', '_blank');
};

onMounted(() => {
  // Animate hero content
  if (heroContentRef.value) {
    animate(heroContentRef.value, {
      opacity: [0, 1],
      translateY: [30, 0],
      duration: 800,
      ease: 'easeOutExpo'
    });
  }

  // Animate image
  if (imageRef.value) {
    animate(imageRef.value, {
      opacity: [0, 1],
      scale: [0.9, 1],
      duration: 800,
      delay: 200,
      ease: 'easeOutExpo'
    });
  }

  setupScrollAnimations();
});

onUnmounted(() => {
  if (observer) {
    observer.disconnect();
  }
});
</script>

<template>
  <GuestLayout>
    <!-- Hero Section -->
    <section id="home" class="min-h-[90vh] flex items-center">
      <div class="max-w-6xl mx-auto px-6 w-full">
        <div class="flex flex-col md:flex-row items-center justify-between gap-16">

          <!-- Left Side - Name & Info -->
          <div ref="heroContentRef" class="flex-1 opacity-0">
            <p class="text-sm uppercase tracking-widest text-gray-500 dark:text-gray-400 mb-4">Full Stack Developer</p>
            <h1 class="text-5xl md:text-7xl font-bold text-black dark:text-white mb-2 leading-tight">
              Meljun Mariquit
            </h1>
            <p class="text-sm uppercase tracking-widest text-gray-500 dark:text-gray-400 mb-6">
              Codename: <span class="text-black dark:text-white font-semibold">ZIN</span>
            </p>
            <p class="text-lg text-gray-600 dark:text-gray-400 mb-10 max-w-md leading-relaxed">
              Building clean, functional, and user-friendly digital experiences.
            </p>

            <div class="flex flex-wrap gap-4">
              <button
                @click="sendEmail"
                class="px-8 py-3 bg-black dark:bg-white text-white dark:text-black font-medium hover:opacity-80 transition-opacity"
              >
                Get in Touch
              </button>
              <button
                @click="downloadCV"
                class="px-8 py-3 border border-black dark:border-white text-black dark:text-white font-medium hover:bg-black hover:text-white dark:hover:bg-white dark:hover:text-black transition-all"
              >
                Download CV
              </button>
            </div>

            <!-- Social Links -->
            <div class="flex gap-6 mt-12">
              <a
                v-for="social in socialLinks"
                :key="social.label"
                :href="social.href"
                target="_blank"
                class="text-gray-400 hover:text-black dark:hover:text-white transition-colors"
              >
                <component :is="social.icon" class="w-5 h-5" />
              </a>
            </div>
          </div>

          <!-- Right Side - Image -->
          <div ref="imageRef" class="flex-1 flex justify-center opacity-0">
            <div class="relative">
              <img
                :src="MeImage"
                alt="Melju Mariquit"
                class="w-72 md:w-96 object-contain grayscale hover:grayscale-0 transition-all duration-500"
              />
              <div class="absolute inset-0 border border-black dark:border-white translate-x-4 translate-y-4 -z-10"></div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="py-24">
      <div ref="projectsRef" class="max-w-6xl mx-auto px-6">
        <h2 class="text-3xl font-bold text-black dark:text-white mb-2 animate-item opacity-0">Projects</h2>
        <p class="text-gray-500 dark:text-gray-400 mb-12 animate-item opacity-0">Selected works</p>

        <div class="grid md:grid-cols-2 gap-8">
          <div class="animate-item opacity-0 group border border-gray-200 dark:border-gray-800 hover:border-black dark:hover:border-white transition-colors">
            <div class="h-48 bg-gray-100 dark:bg-gray-900 flex items-center justify-center">
              <span class="text-6xl font-bold text-gray-200 dark:text-gray-800">01</span>
            </div>
            <div class="p-6">
              <h3 class="text-xl font-bold text-black dark:text-white mb-2">LabTrack: Computer Laboratory Logging System</h3>
              <p class="text-gray-500 dark:text-gray-400 mb-4 text-sm">Automates laboratory access and PC usage monitoring using RFID student ID cards, a centralized Control Station, and a dashboard that logs entry, assigns PCs, and reports technical issues in real-time. Eliminates manual lab management and prevents unauthorized access.</p>
              <div class="flex flex-wrap gap-2">
                <span class="text-xs text-gray-400">Vue.js</span>
                <span class="text-xs text-gray-400">•</span>
                <span class="text-xs text-gray-400">Pinia</span>
                <span class="text-xs text-gray-400">•</span>
                <span class="text-xs text-gray-400">Laravel</span>
                <span class="text-xs text-gray-400">•</span>
                <span class="text-xs text-gray-400">Laravel Reverb</span>
                <span class="text-xs text-gray-400">•</span>
                <span class="text-xs text-gray-400">C#</span>
                <span class="text-xs text-gray-400">•</span>
                <span class="text-xs text-gray-400">RFID</span>
              </div>
            </div>
          </div>

          <div class="animate-item opacity-0 group border border-gray-200 dark:border-gray-800 hover:border-black dark:hover:border-white transition-colors">
            <div class="h-48 bg-gray-100 dark:bg-gray-900 flex items-center justify-center">
              <span class="text-6xl font-bold text-gray-200 dark:text-gray-800">02</span>
            </div>
            <div class="p-6">
              <h3 class="text-xl font-bold text-black dark:text-white mb-2">Employee Attendance Management System</h3>
              <p class="text-gray-500 dark:text-gray-400 mb-4 text-sm">Automates employee attendance using RFID tags scanned through ESP32, logging entry and exit in real-time. Eliminates manual timekeeping errors and ensures accurate attendance records.</p>
              <div class="flex gap-2">
                <span class="text-xs text-gray-400">Vue.js</span>
                <span class="text-xs text-gray-400">•</span>
                <span class="text-xs text-gray-400">Laravel</span>
                <span class="text-xs text-gray-400">•</span>
                <span class="text-xs text-gray-400">Inertia</span>
                <span class="text-xs text-gray-400">•</span>
                <span class="text-xs text-gray-400">ESP32</span>
                <span class="text-xs text-gray-400">•</span>
                <span class="text-xs text-gray-400">RFID</span>
              </div>
            </div>
          </div>

          <div class="animate-item opacity-0 group border border-gray-200 dark:border-gray-800 hover:border-black dark:hover:border-white transition-colors">
            <div class="h-48 bg-gray-100 dark:bg-gray-900 flex items-center justify-center">
              <span class="text-6xl font-bold text-gray-200 dark:text-gray-800">03</span>
            </div>
            <div class="p-6">
              <h3 class="text-xl font-bold text-black dark:text-white mb-2">Cool Project</h3>
              <p class="text-gray-500 dark:text-gray-400 mb-4 text-sm">A brief description of the project and the problem it solves.</p>
              <div class="flex gap-2">
                <span class="text-xs text-gray-400">Python</span>
                <span class="text-xs text-gray-400">•</span>
                <span class="text-xs text-gray-400">Tkinter</span>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Tech Stacks Section -->
    <section id="tech-stacks" class="py-24 bg-gray-50 dark:bg-gray-900/30">
      <div ref="techStacksRef" class="max-w-6xl mx-auto px-6">
        <h2 class="text-3xl font-bold text-black dark:text-white mb-2">Technologies</h2>
        <p class="text-gray-500 dark:text-gray-400 mb-12">Tools I work with</p>

        <div class="grid grid-cols-3 md:grid-cols-6 gap-8">
          <div
            v-for="tech in technologies"
            :key="tech.name"
            class="tech-card opacity-0 flex flex-col items-center gap-3 group"
          >
            <component
              :is="tech.icon"
              class="w-10 h-10 text-gray-400 group-hover:text-black dark:group-hover:text-white transition-colors"
            />
            <span class="text-xs text-gray-500 dark:text-gray-400">{{ tech.name }}</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Certificates Section -->
    <section id="certificates" class="py-24">
      <div ref="certificatesRef" class="max-w-6xl mx-auto px-6">
        <h2 class="text-3xl font-bold text-black dark:text-white mb-2">Certificates</h2>
        <p class="text-gray-500 dark:text-gray-400 mb-12">Professional development</p>

        <div class="space-y-4">
          <div
            v-for="(cert, index) in certificates"
            :key="cert.name"
            class="cert-card opacity-0 flex items-center justify-between py-6 border-b border-gray-200 dark:border-gray-800 group hover:border-black dark:hover:border-white transition-colors"
          >
            <div class="flex items-center gap-6">
              <span class="text-sm text-gray-400">0{{ index + 1 }}</span>
              <div>
                <h3 class="text-lg font-medium text-black dark:text-white">{{ cert.name }}</h3>
                <p class="text-sm text-gray-500 dark:text-gray-400">{{ cert.issuer }}</p>
              </div>
            </div>
            <span class="text-sm text-gray-400">{{ cert.year }}</span>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Section -->
    <section id="contacts" class="py-24 bg-black dark:bg-white">
      <div ref="contactsRef" class="max-w-6xl mx-auto px-6 text-center">
        <h2 class="text-3xl font-bold text-white dark:text-black mb-4 animate-item opacity-0">Let's Work Together</h2>
        <p class="text-gray-400 dark:text-gray-600 mb-10 animate-item opacity-0">Have a project in mind? Let's discuss.</p>

        <a
          href="mailto:meljun.mariquit26@gmail.com"
          class="inline-block px-10 py-4 border border-white dark:border-black text-white dark:text-black font-medium hover:bg-white hover:text-black dark:hover:bg-black dark:hover:text-white transition-all animate-item opacity-0"
        >
          meljun.mariquit26@gmail.com
        </a>

        <div class="flex justify-center gap-8 mt-12 animate-item opacity-0">
          <a
            v-for="social in socialLinks"
            :key="social.label"
            :href="social.href"
            target="_blank"
            class="text-gray-500 hover:text-white dark:hover:text-black transition-colors"
          >
            <component :is="social.icon" class="w-5 h-5" />
          </a>
        </div>
      </div>
    </section>
  </GuestLayout>
</template>
