<script setup>
import { ref, onMounted, onUnmounted } from 'vue';

const isScrolled = ref(false);
const mobileOpen = ref(false);

const handleScroll = () => {
  isScrolled.value = window.scrollY > 50;
};

onMounted(() => window.addEventListener('scroll', handleScroll));
onUnmounted(() => window.removeEventListener('scroll', handleScroll));

const navLinks = [
  { name: 'Inicio', href: '#home' },
  { name: 'Servicios', href: '#services' },
  { name: 'Proyectos', href: '#projects' },
  { name: 'Nosotros', href: '#about' },
  { name: 'Contacto', href: '#contact' },
];
</script>

<template>
  <nav
    :class="[
      'fixed w-full z-50 transition-all duration-500',
      isScrolled
        ? 'bg-black/80 backdrop-blur-xl border-b border-brand-green/20 shadow-[0_4px_30px_rgba(29,94,65,0.15)] py-3'
        : 'bg-black/30 backdrop-blur-md py-5'
    ]"
  >
    <div class="max-w-7xl mx-auto px-6 flex justify-between items-center">
      <!-- Logo -->
      <a href="#home" class="flex items-center group">
        <img
          src="/logo.png"
          alt="Metalúrgica Eblagon"
          class="h-16 w-auto rounded-xl object-contain transition-all duration-300 group-hover:shadow-[0_0_20px_rgba(29,94,65,0.7)] group-hover:scale-105"
        />
      </a>

      <!-- Desktop Links -->
      <div class="hidden md:flex items-center gap-8">
        <a
          v-for="link in navLinks"
          :key="link.name"
          :href="link.href"
          class="font-heading text-white/70 hover:text-white uppercase text-xs tracking-[0.15em] transition-all duration-300 hover:text-brand-green relative group"
        >
          {{ link.name }}
          <span class="absolute -bottom-1 left-0 w-0 h-px bg-brand-green transition-all duration-300 group-hover:w-full"></span>
        </a>
      </div>

      <!-- CTA Button -->
      <div class="hidden md:flex items-center gap-4">
        <a
          href="#contact"
          class="flex items-center gap-2 bg-brand-green hover:bg-[#164d33] text-white font-heading text-xs uppercase tracking-widest px-6 py-3 rounded-full transition-all duration-300 shadow-[0_0_20px_rgba(29,94,65,0.5)] hover:shadow-[0_0_30px_rgba(29,94,65,0.7)] hover:scale-105"
        >
          Pedir Presupuesto
          <svg class="w-4 h-4" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3"/></svg>
        </a>
      </div>

      <!-- Mobile button -->
      <button @click="mobileOpen = !mobileOpen" class="md:hidden text-white hover:text-brand-green transition-colors">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-7 w-7" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path v-if="!mobileOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
          <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
        </svg>
      </button>
    </div>

    <!-- Mobile Menu -->
    <div v-if="mobileOpen" class="md:hidden bg-black/95 backdrop-blur-xl border-t border-brand-green/20 px-6 py-4 flex flex-col gap-4">
      <a
        v-for="link in navLinks"
        :key="link.name"
        :href="link.href"
        @click="mobileOpen = false"
        class="font-heading text-white/80 hover:text-brand-green uppercase text-sm tracking-widest py-2 border-b border-white/5 transition-colors"
      >
        {{ link.name }}
      </a>
      <a href="#contact" @click="mobileOpen = false" class="mt-2 text-center bg-brand-green text-white font-heading text-xs uppercase tracking-widest px-6 py-3 rounded-full">
        Pedir Presupuesto →
      </a>
    </div>
  </nav>
</template>
