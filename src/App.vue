<script setup>
import { ref } from 'vue';
import EnvelopeSection from './components/EnvelopeSection.vue';
import MainSection from './components/MainSection.vue';
import AudioPlayer from './components/AudioPlayer.vue';

const isMusicPlaying = ref(true);
const showSplash = ref(true);
const audioPlayerRef = ref(null);

const toggleMusic = () => {
  isMusicPlaying.value = !isMusicPlaying.value;
};

function enter() {
  showSplash.value = false;
  audioPlayerRef.value?.play();
}
</script>

<template>
  <div class="bg-wedding-beige min-h-screen text-[#333] overflow-x-hidden selection:bg-wedding-blue selection:text-white">
    <!-- Music Player (Global) -->
    <AudioPlayer ref="audioPlayerRef" :isPlaying="isMusicPlaying" @toggle="toggleMusic" />

    <!-- Splash screen -->
    <Transition name="splash-fade">
      <div v-if="showSplash" class="splash" @click="enter" @touchstart.passive="enter">
        <div class="splash-inner">
          <p class="sp-top">¡Nos casamos!</p>
          <h1 class="sp-names">Mija <span class="sp-amp">&amp;</span> Cami</h1>
          <p class="sp-date">16 de Agosto · 3 de Elul</p>
          <div class="sp-tap">
            <svg width="18" height="18" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round">
              <path d="M9 18V12a3 3 0 016 0v1m-6 5h6m-3-11V5"/>
            </svg>
            <span>Tocá para comenzar</span>
          </div>
        </div>
      </div>
    </Transition>

    <!-- Botón de música (fijo arriba a la derecha) -->
    <button
      v-if="!showSplash"
      class="music-btn"
      @click="toggleMusic"
      :title="isMusicPlaying ? 'Pausar música' : 'Reproducir música'"
    >
      <span>♪</span>
      <span class="music-label">{{ isMusicPlaying ? 'ON' : 'OFF' }}</span>
    </button>

    <Transition name="main-enter">
      <main v-if="!showSplash">
        <EnvelopeSection />
        <MainSection />
      </main>
    </Transition>
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

/* ── SPLASH ── */
.splash {
  position: fixed;
  inset: 0;
  z-index: 999;
  background: #3d2b1a;
  display: flex;
  align-items: center;
  justify-content: center;
  cursor: pointer;
  -webkit-tap-highlight-color: transparent;
}
.splash-inner {
  text-align: center;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0;
  user-select: none;
  padding: 0 2rem;
  width: 100%;
}
.sp-top {
  font-family: 'Atteron', serif;
  font-size: 1.4rem;
  letter-spacing: 0.35em;
  text-transform: uppercase;
  color: #f5ede0;
  margin: 0 0 1.5rem;
  opacity: 0.75;
}
.sp-names {
  font-family: 'SouthKorea', cursive;
  font-size: clamp(5.5rem, 22vw, 9rem);
  font-weight: 400;
  color: #f5ede0;
  margin: 0;
  line-height: 1.05;
}
.sp-amp {
  font-family: 'Source Sans 3', sans-serif;
  font-weight: 300;
  font-style: italic;
}
.sp-date {
  font-family: 'Atteron', serif;
  font-size: 1.1rem;
  letter-spacing: 0.25em;
  text-transform: uppercase;
  color: #f5ede0;
  margin: 2rem 0 4rem;
  opacity: 0.75;
}
.sp-tap {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.6rem;
  color: #f5ede0;
  opacity: 0.5;
  font-family: 'Montserrat', sans-serif;
  font-size: 0.65rem;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  animation: sp-pulse 2s ease-in-out infinite;
}
@keyframes sp-pulse {
  0%, 100% { opacity: 0.5; transform: scale(1); }
  50%       { opacity: 0.9; transform: scale(1.04); }
}
.splash-fade-leave-active {
  transition: opacity 1s ease;
}
.splash-fade-leave-to {
  opacity: 0;
}

/* Fade-in del contenido principal */
.main-enter-active {
  transition: opacity 1s ease 0.5s;
}
.main-enter-from {
  opacity: 0;
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
