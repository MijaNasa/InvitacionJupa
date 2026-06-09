<script setup>
import { ref, onMounted } from 'vue'

const flipped    = ref(false)
const visible    = ref(false)
const showScroll = ref(false)

onMounted(() => {
  setTimeout(() => { visible.value = true },   200)
  setTimeout(() => { showScroll.value = true }, 1600)
})

function flipCard() { flipped.value = !flipped.value }

function scrollDown() {
  document.getElementById('main-content')?.scrollIntoView({ behavior: 'smooth' })
}
</script>

<template>
  <section class="card-section">

    <Transition name="card-in">
      <div v-if="visible" class="card-scene" @click="flipCard">
        <div class="card-flipper" :class="{ flipped }">
          <div class="card-face front">
            <img src="/carta-frente.jpeg" alt="Invitación frente" class="card-img" />
          </div>
          <div class="card-face back">
            <img src="/carta-dorso.jpeg" alt="Invitación dorso" class="card-img" />
          </div>
        </div>
        <Transition name="fade">
          <p v-if="!flipped" class="flip-hint">Tocá para ver el dorso &nbsp;↺</p>
          <p v-else class="flip-hint">Tocá para volver &nbsp;↩</p>
        </Transition>
      </div>
    </Transition>

    <Transition name="fade">
      <button
        v-if="showScroll"
        class="scroll-btn"
        @click="scrollDown"
      >
        <span>Más información</span>
        <svg class="w-4 h-4 animate-bounce" fill="none" viewBox="0 0 24 24" stroke="currentColor">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"/>
        </svg>
      </button>
    </Transition>

  </section>
</template>

<style scoped>

/* ── SECTION ── */
.card-section {
  background: #ede8df;
  min-height: 100vh;
  position: relative;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 3rem 1.5rem 5rem;
  overflow: hidden;
}

/* ── CARD SCENE ── */
.card-scene {
  perspective: 1200px;
  cursor: pointer;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 1rem;
}

.card-flipper {
  position: relative;
  width: 320px;
  transform-style: preserve-3d;
  transition: transform 0.85s cubic-bezier(0.4, 0, 0.2, 1);
  border-radius: 6px;
  box-shadow:
    0 2px 4px rgba(80,60,40,0.06),
    0 8px 24px rgba(80,60,40,0.12),
    0 24px 48px rgba(80,60,40,0.10);
}
.card-flipper.flipped {
  transform: rotateY(180deg);
}
.card-flipper:hover {
  box-shadow:
    0 4px 8px rgba(80,60,40,0.08),
    0 16px 40px rgba(80,60,40,0.16),
    0 32px 64px rgba(80,60,40,0.12);
}

.card-face {
  width: 100%;
  backface-visibility: hidden;
  -webkit-backface-visibility: hidden;
  border-radius: 6px;
  overflow: hidden;
}
.card-face.back {
  position: absolute;
  top: 0; left: 0;
  transform: rotateY(180deg);
}
.card-img {
  width: 100%;
  display: block;
}

.flip-hint {
  font-family: 'Montserrat', sans-serif;
  font-size: 0.62rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: #a08060;
  opacity: 0.7;
  user-select: none;
}

/* ── SCROLL ── */
.scroll-btn {
  position: absolute;
  bottom: 1.75rem;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 6px;
  font-family: 'Montserrat', sans-serif;
  font-size: 0.62rem;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  color: #a95c2a;
  background: none;
  border: none;
  cursor: pointer;
  white-space: nowrap;
  transition: color 0.2s;
}
.scroll-btn:hover { color: #7a3f1a; }

/* ── TRANSITIONS ── */
.card-in-enter-active {
  transition: all 1.1s cubic-bezier(0.22, 1, 0.36, 1) 0.3s;
}
.card-in-enter-from {
  opacity: 0;
  transform: translateY(40px) rotateX(12deg) scale(0.94);
}

.fade-enter-active, .fade-leave-active { transition: opacity 0.4s ease; }
.fade-enter-from,  .fade-leave-to      { opacity: 0; }
</style>
