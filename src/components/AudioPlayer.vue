<script setup>
import { ref, onMounted } from 'vue';

const props = defineProps(['isPlaying']);
const emit = defineEmits(['toggle']);

// YouTube video ID from the link: HRdGeSoH3-k
const videoId = "7YLijAtJp9A";
</script>

<template>
  <div v-if="isPlaying" class="fixed bottom-4 left-4 z-50 overflow-hidden rounded-lg shadow-2xl border-4 border-white w-64 aspect-video pointer-events-none opacity-0">
    <!-- Hidden iframe to play music -->
    <iframe 
        width="100%" 
        height="100%" 
        :src="`https://www.youtube.com/embed/${videoId}?autoplay=1&loop=1&playlist=${videoId}`" 
        title="YouTube video player" 
        frameborder="0" 
        allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" 
        referrerpolicy="strict-origin-when-cross-origin" 
        allowfullscreen
    ></iframe>
  </div>

  <!-- Music Toggle Button logic is already in HeroSection, 
       this component just handles the background playback -->
</template>

<style scoped>
/* Hidden play of the video just for audio */
.pointer-events-none {
    user-select: none;
}
</style>
