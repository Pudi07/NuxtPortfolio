<template>
  <div class="min-h-screen bg-gradient-to-br from-gray-900 to-gray-800 text-white">
    <!-- Navigation -->
    <nav class="container mx-auto px-6 py-4 flex justify-between items-center">
      <a href="#" class="text-2xl font-bold">WebDesigner</a>
      <div class="space-x-4">
        <a v-for="item in navItems" :key="item" :href="`#${item.toLowerCase()}`" class="hover:text-purple-400 transition-colors">{{ item }}</a>
      </div>
    </nav>

    <!-- Hero Section -->
    <header class="container mx-auto px-6 py-16 text-center">
      <h1 class="text-5xl md:text-6xl font-extrabold mb-4">Designs That Inspire</h1>
      <p class="text-xl mb-8">Transforming ideas into stunning digital experiences</p>
      <button class="bg-purple-600 hover:bg-purple-700 text-white font-bold py-3 px-6 rounded-full transition-colors">
        Get Started
      </button>
    </header>

    <!-- Services Section -->
    <section id="services" class="container mx-auto px-6 py-16">
      <h2 class="text-3xl font-bold text-center mb-12">My Services</h2>
      <div class="grid grid-cols-1 md:grid-cols-3 gap-8">
        <div v-for="service in services" :key="service.title" class="bg-gray-800 p-6 rounded-lg text-center hover:shadow-lg transition-shadow">
          <component :is="service.icon" class="w-12 h-12 mx-auto mb-4 text-purple-400" />
          <h3 class="text-xl font-semibold mb-2">{{ service.title }}</h3>
          <p class="text-gray-400">{{ service.description }}</p>
        </div>
      </div>
    </section>

    <!-- Projects Section -->
    <section id="projects" class="container mx-auto px-6 py-16">
      <h2 class="text-3xl font-bold text-center mb-12">Recent Projects</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
        <div v-for="project in projects" :key="project.title" class="group relative overflow-hidden rounded-lg">
          <img :src="project.image" :alt="project.title" class="w-full h-64 object-cover transition-transform group-hover:scale-110" />
          <div class="absolute inset-0 bg-gradient-to-t from-black to-transparent opacity-0 group-hover:opacity-100 transition-opacity flex items-end">
            <div class="p-4">
              <h3 class="text-xl font-semibold mb-2">{{ project.title }}</h3>
              <p class="text-sm">{{ project.description }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Testimonials Section -->
    <section id="testimonials" class="container mx-auto px-6 py-16">
      <h2 class="text-3xl font-bold text-center mb-12">What Clients Say</h2>
      <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
        <div v-for="testimonial in testimonials" :key="testimonial.name" class="bg-gray-800 p-6 rounded-lg">
          <p class="mb-4 italic">"{{ testimonial.quote }}"</p>
          <div class="flex items-center">
            <img :src="testimonial.avatar" :alt="testimonial.name" class="w-12 h-12 rounded-full mr-4" />
            <div>
              <h4 class="font-semibold">{{ testimonial.name }}</h4>
              <p class="text-sm text-gray-400">{{ testimonial.position }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Form -->
    <section id="contact" class="container mx-auto px-6 py-16">
      <h2 class="text-3xl font-bold text-center mb-12">Get In Touch</h2>
      <form @submit.prevent="submitForm" class="max-w-lg mx-auto">
        <div class="mb-4">
          <label for="name" class="block mb-2">Name</label>
          <input type="text" id="name" v-model="form.name" required class="w-full px-4 py-2 rounded bg-gray-800 text-white" />
        </div>
        <div class="mb-4">
          <label for="email" class="block mb-2">Email</label>
          <input type="email" id="email" v-model="form.email" required class="w-full px-4 py-2 rounded bg-gray-800 text-white" />
        </div>
        <div class="mb-4">
          <label for="message" class="block mb-2">Message</label>
          <textarea id="message" v-model="form.message" required class="w-full px-4 py-2 rounded bg-gray-800 text-white" rows="4"></textarea>
        </div>
        <button type="submit" class="w-full bg-purple-600 hover:bg-purple-700 text-white font-bold py-3 px-6 rounded transition-colors">
          Send Message
        </button>
      </form>
    </section>

    <!-- Footer -->
    <footer class="bg-gray-900 text-center py-6">
      <p>&copy; 2024 WebDesigner. Pierre Barth</p>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import { LayoutGrid, Palette, Code, Globe } from 'lucide-vue-next'

const navItems = ['Services', 'Projects', 'Testimonials', 'Contact']

const services = [
  { title: 'Web Design', icon: LayoutGrid, description: 'Creating beautiful and functional websites tailored to your needs.' },
  { title: 'UI/UX Design', icon: Palette, description: 'Crafting intuitive user interfaces and seamless user experiences.' },
  { title: 'Web Development', icon: Code, description: 'Building robust and scalable web applications with cutting-edge technologies.' },
  { title: 'SEO Optimization', icon: Globe, description: 'Improving your online visibility and driving organic traffic to your site.' }
]

const projects = [
  { title: 'E-commerce Platform', image: '/placeholder.svg?height=400&width=600', description: 'A fully responsive online store with seamless checkout process.' },
  { title: 'Portfolio Website', image: '/placeholder.svg?height=400&width=600', description: 'A sleek and modern portfolio showcasing creative works.' },
  { title: 'Mobile App UI', image: '/placeholder.svg?height=400&width=600', description: 'User interface design for a productivity mobile application.' }
]

const testimonials = [
  { name: 'John Doe', position: 'CEO, Tech Innovators', quote: 'Working with this web designer was a game-changer for our online presence. Highly recommended!', avatar: '/placeholder.svg?height=100&width=100' },
  { name: 'Jane Smith', position: 'Founder, Creative Studio', quote: 'The attention to detail and creativity in the design process was impressive. Our website looks stunning!', avatar: '/placeholder.svg?height=100&width=100' }
]

const form = ref({
  name: '',
  email: '',
  message: ''
})

const submitForm = () => {
  // Handle form submission logic here
  console.log('Form submitted:', form.value)
  // Reset form after submission
  form.value = { name: '', email: '', message: '' }
}
</script>

<style scoped>
/* Add any additional styles here */
</style>