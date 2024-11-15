<template>
  <div :class="{ 'dark': isDarkMode }" class="min-h-screen bg-white dark:bg-gray-900 text-gray-900 dark:text-white transition-colors duration-300">
    <!-- Navigation -->
    <nav class="container mx-auto px-6 py-4 flex justify-between items-center sticky top-0 z-10 bg-white dark:bg-gray-900 " :class="{'shadow-md': isScrolled}">
      <a href="#" class="text-2xl font-bold">Pierre Barth</a>
      <div class="flex items-center space-x-4">
        <div v-for="item in navItems" :key="item">
          <a :href="`#${item.toLowerCase()}`" class="hover:text-purple-600 dark:hover:text-purple-400 transition-colors">{{ item }}</a>
        </div>
        <button @click="toggleDarkMode" class="p-2 rounded-full bg-gray-200 dark:bg-gray-700 transition-colors">
          <SunIcon v-if="isDarkMode" class="w-5 h-5" />
          <MoonIcon v-else class="w-5 h-5" />
        </button>
      </div>
    </nav>

    <!-- Hero Section -->
    <header class="container mx-auto px-6 py-16 text-center">
      <h1 class="text-5xl md:text-6xl font-extrabold mb-4">Des designs qui inspirent</h1>
      <p class="text-xl mb-8">Transformer des idées en expériences numériques époustouflantes</p>
      <button class="bg-purple-600 hover:bg-purple-700 text-white font-bold py-3 px-6 rounded-full transition-colors">
        <a href=#contact>
        Contactez-moi
        </a>
      </button>
    </header>

    <!-- Services Section -->
    <section id="services" class="container mx-auto px-6 py-16">
      <h2 class="text-3xl font-bold text-center mb-12">Mes Services</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
        <div v-for="service in services" :key="service.title" class="bg-gray-100 dark:bg-gray-800 p-6 rounded-lg text-center hover:shadow-lg transition-shadow">
          <component :is="service.icon" class="w-12 h-12 mx-auto mb-4 text-purple-600 dark:text-purple-400" />
          <h3 class="text-xl font-semibold mb-2">{{ service.title }}</h3>
          <p class="text-gray-600 dark:text-gray-400">{{ service.description }}</p>
        </div>
      </div>
    </section>

    <!-- Projects Section -->
    <section id="projets" class="container mx-auto px-6 py-16">
      <h2 class="text-3xl font-bold text-center mb-12">Projets recents</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div v-for="project in projects" :key="project.title" class="group relative overflow-hidden rounded-lg">
          <a :href="project.link" target="_blank" rel="noopener noreferrer">
          <img 
          :src="project.image" 
          :alt="project.title"
          class="w-full h-64 object-cover transition-transform group-hover:scale-105"
          loading="lazy"
        />
          <div class="absolute inset-0 bg-gradient-to-t from-black to-transparent opacity-0 group-hover:opacity-100 transition-opacity flex items-end">
            <div class="p-4">
              <h3 class="text-xl font-semibold mb-2 text-white">{{ project.title }}</h3>
              <p class="text-sm text-gray-200">{{ project.description }}</p>
            </div>
          </div>
        </a>
        </div>
      </div>
    </section>

    <!-- Testimonials Section -->
    <section id="avis" class="container mx-auto px-6 py-16">
      <h2 class="text-3xl font-bold text-center mb-12">Ce que disent les clients</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
        <div v-for="testimonial in testimonials" :key="testimonial.name" class="bg-gray-100 dark:bg-gray-800 p-6 rounded-lg">
          <p class="mb-4 italic">"{{ testimonial.quote }}"</p>
          <div class="flex items-center">
            <img :src="testimonial.avatar" :alt="testimonial.name" class="w-12 h-12 rounded-full mr-4" />
            <div>
              <h4 class="font-semibold">{{ testimonial.name }}</h4>
              <p class="text-sm text-gray-600 dark:text-gray-400">{{ testimonial.position }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Form -->
    <!-- Contact Form -->
<section id="contact" class="container mx-auto px-6 py-16">
  <h2 class="text-3xl font-bold text-center mb-12">Prenez contact</h2>

  <form action="https://formspree.io/f/mdkozvej" method="POST" class="max-w-lg mx-auto">
    <div class="mb-4">
      <label for="name" class="block mb-2">Name</label>
      <input 
        type="text" 
        id="name" 
        name="name" 
        required 
        class="w-full px-4 py-2 rounded bg-gray-100 dark:bg-gray-800 text-gray-900 dark:text-white border border-gray-300 dark:border-gray-700" 
      />
    </div>
    <div class="mb-4">
      <label for="email" class="block mb-2">Email</label>
      <input 
        type="email" 
        id="email" 
        name="email" 
        required 
        class="w-full px-4 py-2 rounded bg-gray-100 dark:bg-gray-800 text-gray-900 dark:text-white border border-gray-300 dark:border-gray-700" 
      />
    </div>
    <div class="mb-4">
      <label for="message" class="block mb-2">Message</label>
      <textarea 
        id="message" 
        name="message" 
        required 
        class="w-full px-4 py-2 rounded bg-gray-100 dark:bg-gray-800 text-gray-900 dark:text-white border border-gray-300 dark:border-gray-700" 
        rows="4">
      </textarea>
    </div>
    <button type="submit" class="w-full bg-purple-600 hover:bg-purple-700 text-white font-bold py-3 px-6 rounded transition-colors">
      Send Message
    </button>
  </form>
</section>


    <!-- Footer -->
    <footer class="bg-gray-200 dark:bg-gray-800 py-6">
      <div class="container mx-auto px-6 flex justify-between items-center">
        <p>&copy; 2024 Pierre Barth.</p>
        <div class="flex items-center space-x-4">
          <a href="mailto:contact@webdesigner.com" class="hover:text-purple-600 dark:hover:text-purple-400 transition-colors">
            contact@pierre-barth.fr
          </a>
          <span>|</span>
          <a href="https://www.linkedin.com/in/barth-pierre/" class="hover:text-purple-600 dark:hover:text-purple-400 transition-colors">
            LinkedIn
          </a>
        </div>
      </div>
    </footer>

  </div>
</template>

<script setup>
import { ref } from 'vue'
import { LayoutGrid, Palette, Code, Globe, Sun as SunIcon, Moon as MoonIcon } from 'lucide-vue-next'

import projet1 from '~/assets/img/projet1.png';
import projet2 from '~/assets/img/projet2.png';
import avatar1 from '~/assets/img/37.png';
import avatar2 from '~/assets/img/58.png';

useHead({
  title: 'Pierre Barth - Web Designer Freelance',
  meta: [
    { name: 'description', content: 'Web designer freelance spécialisé dans la conception de sites web modernes et fonctionnels.' },
    { name: 'keywords', content: 'web design, web development, freelance, portfolio' }
  ]
})

const isDarkMode = ref(false)
const isScrolled = ref(false)

const toggleDarkMode = () => {
  isDarkMode.value = !isDarkMode.value
  if (isDarkMode.value) {
    document.documentElement.classList.add('dark')
  } else {
    document.documentElement.classList.remove('dark')
  }
}

// Scroll event listener to toggle shadow
const checkScroll = () => {
  isScrolled.value = window.scrollY > 50;
};

onMounted(() => {
  window.addEventListener('scroll', checkScroll);
});

onBeforeUnmount(() => {
  window.removeEventListener('scroll', checkScroll);
});

const navItems = ['Services', 'Projets', 'Avis', 'Contact']

const services = [
  { title: 'Conception de Sites Web', icon: LayoutGrid, description: 'Création de sites web beaux et fonctionnels adaptés à vos besoins.' },
  { title: 'Conception UI/UX', icon: Palette, description: 'Création d’interfaces utilisateur intuitives et d’expériences utilisateurs fluides.' },
  { title: 'Développement Web', icon: Code, description: 'Développement d’applications web robustes et évolutives avec des technologies de pointe.' },
  { title: 'Optimisation SEO', icon: Globe, description: 'Amélioration de votre visibilité en ligne et génération de trafic organique vers votre site.' }
]

const projects = [
{ 
    title: 'Site Portfolio FullPage', 
    image: projet1, 
    description: 'Un site portfolio moderne et minimaliste conçu avec Vue 3 et la librairie de défilement FullPage' ,
    link: 'https://pierre-barth.fr/' 
  },
  { 
    title: 'Site de ressources pédagogiques', 
    image: projet2, 
    description: 'Un site web éducatif interactif pour les étudiants et les enseignants',
    link: 'https://pedagogie.orgnac.com/'
  },
]

const testimonials = [
  { name: 'John Doe', position: 'CEO, Tech Innovators', quote: '“Travailler avec Pierre a été une expérience incroyable. Il a su comprendre mes besoins et créer un site vitrine qui représente parfaitement mon entreprise. Très satisfait du résultat !”', avatar: avatar1 },
  { name: 'Jane Smith', position: 'Founder, Creative Studio', quote: 'Nous avons pu lancer notre boutique en ligne en un temps record. Le site est moderne, fluide et les ventes ont augmenté grâce à l’optimisation SEO', avatar: avatar2 }
]

</script>

<style>
html, body {
  height: 100%;
}

/* Smooth scrolling for anchor links */
html {
  scroll-behavior: smooth;
  scroll-padding-top: 2em;
}

nav {
  transition: box-shadow 0.3s ease-in-out;
}

::-webkit-scrollbar {
  width: 9px;
  height: 9px;
}

::-webkit-scrollbar-track {
  background: #ddd;
  border-radius: 10px;
}

::-webkit-scrollbar-thumb {
  background: #bbb ;
  border-radius: 10px;
}

::-webkit-scrollbar-thumb:hover {
  background: #9333ea ;
}

/* Mode sombre */
html.dark ::-webkit-scrollbar-track {
  background: #333;
}

html.dark ::-webkit-scrollbar-thumb {
  background: #555;
}

html.dark ::-webkit-scrollbar-thumb:hover {
  background: #9333ea ;
}



</style>