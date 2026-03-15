<script setup>
defineProps(['isMusicPlaying']);
defineEmits(['toggleMusic']);
</script>

<template>
  <section class="min-h-screen flex flex-col items-center justify-center relative px-6 text-center pt-20">
    <!-- Floating Music Button (Top Right-ish like screenshot) -->
    <button 
      @click="$emit('toggleMusic')"
      class="fixed top-8 right-8 z-50 w-12 h-12 rounded-full bg-wedding-blue text-white flex items-center justify-center shadow-lg transition-transform hover:scale-110 active:scale-95"
    >
      <span v-if="!isMusicPlaying">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 19V6l12-3v13M9 19c0 1.105-1.343 2-3 2s-3-.895-3-2 1.343-2 3-2 3 .895 3 2zm12-3c0 1.105-1.343 2-3 2s-3-.895-3-2 1.343-2 3-2 3 .895 3 2zM9 10l12-3" />
        </svg>
      </span>
      <span v-else class="flex gap-1 items-end h-4">
        <span class="w-1 bg-white animate-[music-bar_0.6s_ease-in-out_infinite_alternate]"></span>
        <span class="w-1 bg-white animate-[music-bar_0.8s_ease-in-out_infinite_alternate]"></span>
        <span class="w-1 bg-white animate-[music-bar_0.5s_ease-in-out_infinite_alternate]"></span>
      </span>
    </button>

    <!-- Champagne Toast Illustration -->
    <div class="mb-8 w-full max-w-sm mx-auto">
      <img 
        src="/wedding_toast_illustration_1773595169468.png" 
        alt="Brindis" 
        class="w-full h-auto drop-shadow-sm opacity-90"
      />
    </div>

    <!-- Wedding Names -->
    <div class="mb-4">
      <h1 class="script-text block mb-1">Cami</h1>
      <span class="text-wedding-blue text-3xl font-display font-light">y</span>
      <h1 class="script-text block mt-1">Mija</h1>
    </div>

    <!-- Subtitle -->
    <div class="mt-8 mb-2">
      <p class="uppercase tracking-[0.3em] text-sm text-wedding-blue/80 font-semibold animate-pulse">
        Llegó el día
      </p>
    </div>

    <!-- Scroll Indicator -->
    <div class="absolute bottom-10 left-1/2 -translate-x-1/2 animate-bounce">
        <svg xmlns="http://www.w3.org/2000/svg" class="h-8 w-8 text-wedding-accent" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
        </svg>
    </div>
  </section>
</template>

<style scoped>
@keyframes music-bar {
  from { height: 4px; }
  to { height: 16px; }
}
</style>
