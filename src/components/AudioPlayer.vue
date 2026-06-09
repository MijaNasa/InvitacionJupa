<script setup>
import { ref, watch, onMounted } from 'vue'

const props = defineProps(['isPlaying'])
const audio = ref(null)

onMounted(() => {
  audio.value.volume = 0.7

  // Intenta autoplay; si el browser lo bloquea (iOS), reintenta en el primer gesto
  audio.value.play().catch(() => {
    const retry = () => {
      if (props.isPlaying) audio.value.play().catch(() => {})
      document.removeEventListener('click', retry)
      document.removeEventListener('touchstart', retry)
    }
    document.addEventListener('click', retry)
    document.addEventListener('touchstart', retry, { passive: true })
  })
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
