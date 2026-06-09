<script setup>
import { ref, watch, onMounted } from 'vue'

const props = defineProps(['isPlaying'])
const audio = ref(null)

onMounted(() => {
  audio.value.volume = 0.7
  // Intenta autoplay (funciona en desktop); en iOS falla y el splash se encarga
  audio.value.play().catch(() => {})
})

watch(() => props.isPlaying, (playing) => {
  if (!audio.value) return
  if (playing) {
    audio.value.play().catch(() => {})
  } else {
    audio.value.pause()
  }
})

function play() {
  if (audio.value) audio.value.play().catch(() => {})
}

defineExpose({ play })
</script>

<template>
  <audio ref="audio" src="/cancion.mp3" loop preload="auto" />
</template>
