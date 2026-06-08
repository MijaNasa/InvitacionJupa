<script setup>
import { ref, onMounted } from 'vue';
import EnvelopeSection from './components/EnvelopeSection.vue';
import MainSection from './components/MainSection.vue';
import AudioPlayer from './components/AudioPlayer.vue';

const isMusicPlaying = ref(true);

const toggleMusic = () => {
  isMusicPlaying.value = !isMusicPlaying.value;
};

// Los navegadores bloquean autoplay sin interacción previa.
// En el primer click/touch recreamos el iframe para que el autoplay funcione.
onMounted(() => {
  const startOnInteraction = () => {
    isMusicPlaying.value = false;
    setTimeout(() => { isMusicPlaying.value = true; }, 50);
    document.removeEventListener('click', startOnInteraction);
    document.removeEventListener('touchstart', startOnInteraction);
  };
  document.addEventListener('click', startOnInteraction);
  document.addEventListener('touchstart', startOnInteraction);
});
</script>

<template>
  <div class="bg-wedding-beige min-h-screen text-[#333] overflow-x-hidden selection:bg-wedding-blue selection:text-white">
    <!-- Music Player (Global) -->
    <AudioPlayer :isPlaying="isMusicPlaying" @toggle="toggleMusic" />

    <!-- Botón de música (fijo arriba a la derecha) -->
    <button
      class="music-btn"
      @click="toggleMusic"
      :title="isMusicPlaying ? 'Pausar música' : 'Reproducir música'"
    >
      <span v-if="isMusicPlaying">♪</span>
      <span v-else>♪</span>
      <span class="music-label">{{ isMusicPlaying ? 'ON' : 'OFF' }}</span>
    </button>

    <main>
      <!-- Envelope Animation (intro) -->
      <EnvelopeSection />

      <!-- Main content — scroll target from envelope -->
      <MainSection />

    </main>
<!-- 
    Footer decoration
    <footer class="py-12 flex justify-center opacity-30">
        <img src="/wedding_arch.png" class="w-24 h-auto" />
    </footer> -->
  </div>
</template>

<style>
/* Global Wedding Styles */
* {
  box-sizing: border-box;
}

.music-btn {
  position: fixed;
  top: 14px;
  right: 14px;
  z-index: 100;
  background: rgba(255,255,255,0.85);
  backdrop-filter: blur(6px);
  border: 1px solid rgba(201,169,110,0.4);
  border-radius: 20px;
  padding: 6px 12px;
  font-size: 13px;
  color: #5a3e2b;
  cursor: pointer;
  display: flex;
  align-items: center;
  gap: 5px;
  box-shadow: 0 2px 10px rgba(0,0,0,0.1);
  transition: background 0.2s;
  font-family: 'Montserrat', sans-serif;
}
.music-btn:hover { background: rgba(255,255,255,0.95); }
.music-label {
  font-size: 9px;
  letter-spacing: 0.1em;
  font-weight: 600;
  opacity: 0.7;
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
        rgba(185, 204, 220, 0.15) 40px,
        rgba(185, 204, 220, 0.15) 80px
    );
}
</style>
