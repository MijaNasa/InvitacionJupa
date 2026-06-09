<script setup>
import { ref, watch, onMounted } from 'vue'

const props = defineProps(['isPlaying'])
const audio = ref(null)

onMounted(() => {
  audio.value.volume = 0.7
})

watch(() => props.isPlaying, (playing) => {
  if (!audio.value) return
  if (playing) {
    audio.value.play().catch(() => {})
  } else {
    audio.value.pause()
  }
})
</script>

<template>
  <audio ref="audio" src="/cancion.mp3" loop preload="auto" />
</template>
