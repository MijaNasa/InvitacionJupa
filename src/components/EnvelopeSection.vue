<script setup>
import { ref } from 'vue'

const state = ref('idle') // idle → opening → done
const flipped = ref(false)

const FLAP_MS  = 1800
const PAUSE_MS = 250
const CARD_MS  = 2800

function startAnimation() {
  if (state.value !== 'idle') return
  state.value = 'opening'
  setTimeout(() => { state.value = 'done' }, FLAP_MS + PAUSE_MS + CARD_MS)
}

function flipCard() {
  if (state.value !== 'done') return
  flipped.value = !flipped.value
}

function scrollDown() {
  document.getElementById('main-content')?.scrollIntoView({ behavior: 'smooth' })
}
</script>

<template>
  <section class="min-h-screen flex flex-col items-center justify-start relative overflow-hidden px-4 pt-10">

    <div class="absolute inset-0" style="background:#ede8df;">
      <div class="absolute inset-0"
        style="background-image:url('/hero-bg.png');background-size:cover;background-position:center;opacity:.06"/>
    </div>

    <div class="relative z-10 flex flex-col items-center w-full">

      <p class="font-display text-[10px] tracking-[0.35em] text-[#8b7355] uppercase mb-6">בעזרת ה׳</p>

      <!-- ESCENA -->
      <div class="scene">

        <!-- CARTA (detrás del sobre en z-index, cubierta por los pliegues) -->
        <div
          class="card-wrapper"
          :class="{ rising: state === 'opening', risen: state === 'done' }"
          @click="flipCard"
        >
          <div class="card-flipper" :class="{ flipped }">
            <!-- FRENTE -->
            <div class="card-face front">
              <img src="/carta-frente.jpeg" alt="Invitación frente" class="card-img" />
            </div>
            <!-- DORSO -->
            <div class="card-face back">
              <img src="/carta-dorso.jpeg" alt="Invitación dorso" class="card-img" />
            </div>
          </div>
          <div v-if="state === 'done' && !flipped" class="flip-hint">Tocá para girar</div>
        </div>

        <!-- SOBRE -->
        <div
          class="envelope"
          :class="{ opened: state !== 'idle' }"
          @click="startAnimation"
        >
          <div class="env-body">
            <!-- líneas de costura de los pliegues -->
            <svg class="env-seams" xmlns="http://www.w3.org/2000/svg">
              <line x1="0"    y1="0"    x2="50%" y2="52%" class="seam-top"/>
              <line x1="100%" y1="0"    x2="50%" y2="52%" class="seam-top"/>
              <line x1="0"    y1="100%" x2="50%" y2="52%" class="seam-bot"/>
              <line x1="100%" y1="100%" x2="50%" y2="52%" class="seam-bot"/>
            </svg>
            <div class="env-liner"></div>
            <div class="env-fold-left"></div>
            <div class="env-fold-right"></div>
            <div class="env-fold-bottom"></div>
          </div>
          <div class="env-flap" :class="{ 'is-open': state !== 'idle' }"></div>
          <!-- Nombres visibles cuando está cerrado -->
          <Transition name="fade">
            <div v-if="state === 'idle'" class="env-names">
              <span>FAMILIA NASATSKY</span>
              <span>FAMILIA EBLAGON</span>
            </div>
          </Transition>
        </div>

        <!-- CTA abrir -->
        <Transition name="fade">
          <div v-if="state === 'idle'" class="cta" @click="startAnimation">
            Tocá para abrir
            <span class="cta-arrow">↓</span>
          </div>
        </Transition>

      </div>
      <!-- /scene -->

      <!-- Ver la invitación -->
      <Transition name="fade">
        <button
          v-if="state === 'done'"
          class="mt-6 flex flex-col items-center gap-2 text-[#a95c2a] hover:text-[#7a3f1a] transition-colors"
          @click="scrollDown"
        >
          <span class="text-[11px] tracking-[0.3em] uppercase">Mas informacion</span>
          <svg class="w-5 h-5 animate-bounce" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"/>
          </svg>
        </button>
      </Transition>

    </div>
  </section>
</template>

<style scoped>

/* ── VARIABLES ── */
:root {
  --env-blue: #f0ebe1;
  --env-dark: #ddd5c4;
  --env-lite: #f8f4ee;
  --gold:     #c9a96e;
  --text:     #5a3e2b;
  --shadow:   rgba(80, 60, 40, 0.22);
}

/* ── SCENE ── */
.scene {
  position: relative;
  width: 420px;
  height: 500px;
  display: flex;
  align-items: flex-end;
  justify-content: center;
}

/* ── ENVELOPE ── */
.envelope {
  position: absolute;
  bottom: 0;
  width: 380px;
  height: 230px;
  border-radius: 4px;
  filter: drop-shadow(0 18px 40px var(--shadow));
  cursor: pointer;
  animation: env-appear 0.9s cubic-bezier(0.22, 1, 0.36, 1) 0.3s both;
}

.env-body {
  position: absolute;
  inset: 0;
  background: var(--env-blue);
  border-radius: 4px;
  overflow: hidden;
}
.env-body::after {
  content: '';
  position: absolute; inset: 0;
  box-shadow: inset 0 -10px 20px rgba(0,0,0,0.08), inset 0 10px 16px rgba(255,255,255,0.15);
  pointer-events: none;
}

.env-seams {
  position: absolute;
  inset: 0;
  width: 100%;
  height: 100%;
  z-index: 7;
  pointer-events: none;
}
.seam-top {
  stroke: rgba(0,0,0,0.08);
  stroke-width: 0.8;
}
.seam-bot {
  stroke: rgba(255,255,255,0.6);
  stroke-width: 0.8;
}

.env-fold-left,
.env-fold-right,
.env-fold-bottom {
  position: absolute; inset: 0; z-index: 6;
}
.env-fold-left   { background: var(--env-dark); clip-path: polygon(0 0, 50% 52%, 0 100%); }
.env-fold-right  { background: var(--env-lite); clip-path: polygon(100% 0, 50% 52%, 100% 100%); }
.env-fold-bottom { background: var(--env-blue); clip-path: polygon(0 100%, 100% 100%, 50% 52%); filter: brightness(0.92); }

.env-liner {
  position: absolute; inset: 0;
  background: linear-gradient(170deg, #c8ba60 0%, #ede090 40%, #f5eea8 65%, #d4c468 100%);
  clip-path: polygon(0 0, 100% 0, 50% 52%);
  opacity: 0;
  transition: opacity 0.5s ease 0.2s;
}
.opened .env-liner { opacity: 1; }

.env-flap {
  position: absolute; inset: 0;
  background: linear-gradient(180deg, #f8f5ee 0%, #ede8de 100%);
  clip-path: polygon(0 0, 100% 0, 50% 52%);
  transform-origin: top center;
  transform: perspective(1000px) rotateX(0deg);
  filter: brightness(1.0);
  z-index: 10;
}
.env-flap.is-open {
  animation: flap-open 1.8s cubic-bezier(0.45, 0, 0.35, 1) forwards;
}

.env-names {
  position: absolute; inset: 0; z-index: 7;
  display: flex; align-items: flex-end; justify-content: space-between;
  padding: 0 10% 18%;
  font-family: 'Playfair Display', serif;
  font-size: 0.55rem; letter-spacing: .13em; color: #c9762e;
  pointer-events: none;
}

/* ── CARD WRAPPER ── */
.card-wrapper {
  position: absolute;
  width: 350px;
  bottom: 30px;
  left: 50%;
  /* empieza centrada dentro del sobre, invisible */
  transform: translateX(-50%) translateY(0px) scale(0.82);
  opacity: 0;
  z-index: 5;
  pointer-events: none;
  will-change: transform, opacity;
  perspective: 1200px;
}

.card-flipper {
  position: relative;
  width: 100%;
  transform-style: preserve-3d;
  transition: transform 0.75s cubic-bezier(0.4, 0, 0.2, 1);
  cursor: default;
}
.card-wrapper.risen .card-flipper {
  cursor: pointer;
}
.card-flipper.flipped {
  transform: rotateY(180deg);
}

/* ── CARD FACE ── */
.card-face {
  width: 100%;
  height: 100%;
  background: #f5f0e8;
  border: 1px solid #ddd4c0;
  border-radius: 3px;
  box-shadow: 0 8px 32px var(--shadow);
  backface-visibility: hidden;
  -webkit-backface-visibility: hidden;
  overflow: hidden;
  position: relative;
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

/* shine sweep */
.card-face::after {
  content: '';
  position: absolute; inset: 0;
  background: linear-gradient(110deg, transparent 25%, rgba(255,255,255,0.55) 50%, transparent 75%);
  transform: translateX(-150%);
  pointer-events: none;
  z-index: 2;
}
.card-wrapper.risen .card-face.front::after {
  animation: shine 0.9s ease 0.2s forwards;
}

/* ── ESTADOS DE LA CARTA ── */
.card-wrapper.rising {
  animation: card-rise 2.8s cubic-bezier(0.25, 0.46, 0.45, 0.94) 2.05s forwards;
}
.card-wrapper.risen {
  transform: translateX(-50%) translateY(-60px) scale(1.0);
  opacity: 1;
  pointer-events: auto;
  z-index: 20;
}

/* ── FLIP HINT ── */
.flip-hint {
  position: absolute;
  bottom: -28px;
  left: 50%;
  transform: translateX(-50%);
  font-size: 8px;
  letter-spacing: 0.3em;
  color: var(--text);
  opacity: 0.5;
  white-space: nowrap;
  text-transform: uppercase;
  pointer-events: none;
  animation: hint-pulse 2.5s ease-in-out 1s infinite;
}

/* ── CTA ── */
.cta {
  position: absolute;
  bottom: -52px;
  left: 50%;
  transform: translateX(-50%);
  font-size: 9px;
  letter-spacing: 0.35em;
  color: var(--text);
  text-transform: uppercase;
  cursor: pointer;
  white-space: nowrap;
  user-select: none;
  text-align: center;
}
.cta-arrow {
  display: block;
  text-align: center;
  margin-top: 6px;
  font-size: 14px;
  animation: bounce 1.4s ease-in-out infinite;
}

/* ── KEYFRAMES ── */
@keyframes env-appear {
  from { opacity: 0; transform: translateY(30px) scale(0.96); }
  to   { opacity: 1; transform: translateY(0) scale(1); }
}

@keyframes flap-open {
  0%   { transform: perspective(1000px) rotateX(0deg); }
  100% { transform: perspective(1000px) rotateX(-180deg); }
}

@keyframes card-rise {
  0%   { transform: translateX(-50%) translateY(0px)    scale(0.82); opacity: 1; }
  45%  { transform: translateX(-50%) translateY(-220px) scale(1.0);  opacity: 1; }
  55%  { transform: translateX(-50%) translateY(-230px) scale(1.01); opacity: 1; }
  100% { transform: translateX(-50%) translateY(-60px)  scale(1.0);  opacity: 1; }
}

@keyframes shine {
  to { transform: translateX(150%); }
}

@keyframes bounce {
  0%, 100% { transform: translateY(0); }
  50%       { transform: translateY(4px); }
}

@keyframes hint-pulse {
  0%, 100% { opacity: 0.5; }
  50%       { opacity: 0.2; }
}

/* ── TRANSITIONS ── */
.fade-enter-active, .fade-leave-active { transition: opacity .4s ease; }
.fade-enter-from,  .fade-leave-to      { opacity: 0; }
</style>
