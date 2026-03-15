<script setup>
import { ref, onMounted } from 'vue';
import HeroSection from './components/HeroSection.vue';
import CeremonySection from './components/CeremonySection.vue';
import GallerySection from './components/GallerySection.vue';
import RSVPSection from './components/RSVPSection.vue';
import CalendarSection from './components/CalendarSection.vue';
import AudioPlayer from './components/AudioPlayer.vue';

const isMusicPlaying = ref(false);

const toggleMusic = () => {
  isMusicPlaying.value = !isMusicPlaying.value;
};
</script>

<template>
  <div class="bg-wedding-beige min-h-screen text-[#333] overflow-x-hidden selection:bg-wedding-blue selection:text-white">
    <!-- Music Player (Global) -->
    <AudioPlayer :isPlaying="isMusicPlaying" @toggle="toggleMusic" />

    <main>
      <!-- Hero Section -->
      <HeroSection :isMusicPlaying="isMusicPlaying" @toggleMusic="toggleMusic" />
      
      <!-- Ceremony & Party Section -->
      <CeremonySection />
      
      <!-- Photo Gallery -->
      <GallerySection />
      
      <!-- RSVP & Dress Code -->
      <RSVPSection />

    </main>

    <!-- Footer decoration -->
    <footer class="py-12 flex justify-center opacity-30">
        <img src="/wedding_arch.png" class="w-24 h-auto" />
    </footer>
  </div>
</template>

<style>
/* Global Wedding Styles */
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  padding: 0;
  overflow-x: hidden;
}

/* Background Stripe Pattern Like Screenshot */
.bg-wedding-beige {
    background-image: repeating-linear-gradient(
        90deg,
        transparent,
        transparent 40px,
        rgba(125, 211, 252, 0.1) 40px,
        rgba(125, 211, 252, 0.1) 80px
    );
}
</style>
