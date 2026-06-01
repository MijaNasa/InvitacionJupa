<script setup>
import { ref, watch } from 'vue'

const stage     = ref('closed')
const cardFront = ref(false)

function openEnvelope() {
  if (stage.value !== 'closed') return
  stage.value = 'opening'
  setTimeout(() => { stage.value = 'card' }, 1300)
}
function flipCard() {
  if (stage.value === 'card')         stage.value = 'flipped'
  else if (stage.value === 'flipped') stage.value = 'card'
}
function scrollDown() {
  document.getElementById('main-content')?.scrollIntoView({ behavior: 'smooth' })
}

/*
  Z-index switch at animation peak (~2.2 s after stage = 'card'):
    false → card z:0, envelope z:2  → envelope hides card   ("inside")
    true  → card z:5, envelope z:2  → card in front         ("emerged")
  The switch happens when card is fully above the envelope, so no visible pop.
*/
watch(stage, (v) => {
  if (v === 'card') setTimeout(() => { cardFront.value = true  }, 2200)
  if (v === 'closed')                  cardFront.value = false
})
</script>

<template>
  <section class="min-h-screen flex flex-col items-center justify-center relative overflow-hidden py-12 px-4">

    <div class="absolute inset-0 bg-[#f0ebe2]">
      <div class="absolute inset-0"
        style="background-image:url('/hero-bg.png');background-size:cover;background-position:center;opacity:.1"/>
    </div>

    <div class="relative z-10 flex flex-col items-center w-full gap-0">

      <p class="font-display text-[10px] tracking-[0.35em] text-[#8b7355] uppercase mb-8">בעזרת ה׳</p>

      <!--
        ENV-STAGE: only the envelope height participates in flex layout.
        This makes justify-center center the envelope in the viewport.
        The card is position:absolute inside, extending upward without
        affecting layout height.
      -->
      <div class="env-stage">

        <!-- ── CARD (absolute, grows upward from bottom of stage) ── -->
        <div
          class="card-slot"
          :class="stage !== 'closed' ? 'card-risen' : 'card-hidden'"
          :style="{ zIndex: cardFront ? 5 : 0 }"
        >
          <div class="card-perspective">
            <div class="card-flipper"
              :class="{ 'is-flipped': stage === 'flipped' }"
              @click="flipCard"
            >
              <!-- FRONT -->
              <div class="card-face front">
                <p class="c-bh">ב״ה</p>
                <p class="c-intro">
                  Con gratitud y alabanzas a Hashem,<br>
                  tenemos el agrado de invitar<br>
                  a Usted al enlace de nuestros queridos hijos
                </p>
                <div class="c-names">Cami <span>&amp;</span> Mija</div>
                <div class="c-rule"></div>
                <p class="c-detail">
                  Domingo 16 de Agosto de 2026<br>
                  ט"ו מנחם אב תשפ"ו
                </p>
                <p class="c-detail mt-2">
                  Salón Estancia Pizarro<br>
                  Av. Ejército Argentino 47, La Calera, Córdoba
                </p>
                <p class="c-detail mt-2">
                  Kabalát Paním: <strong>16:30 hs.</strong> &nbsp;·&nbsp; La Jupá: <strong>17:00 hs.</strong>
                </p>
                <div class="c-families">
                  <div><p>Familia</p><p class="font-semibold">[Nombre 1]</p></div>
                  <div><p>Familia</p><p class="font-semibold">[Nombre 2]</p></div>
                </div>
                <p class="c-flip-hint">Tocá para ver en hebreo →</p>
                <!-- spacer: sits inside the envelope pocket -->
                <div class="c-spacer"></div>
              </div>

              <!-- BACK (Hebrew) -->
              <div class="card-face back" dir="rtl">
                <p class="c-bh">בעזה"י</p>
                <p class="c-detail mt-4 leading-loose text-right">
                  אנו מודים לד' על כל הטוב אשר גמלנו,<br>
                  ובחסדו הגדול זכינו בנשואי יקירינו
                </p>
                <div class="c-names mt-3">מיה <span dir="ltr">&amp;</span> קאמי</div>
                <div class="c-rule"></div>
                <p class="c-detail leading-loose text-right">
                  החופה תהיה בעזה"י<br>
                  יום ראשון, ט"ו מנחם אב תשפ"ו<br>
                  16 de Agosto de 2026<br><br>
                  אולם אסטנסיה פיזארו<br>
                  La Calera, Córdoba<br><br>
                  קבלת פנים: 16:30<br>
                  החופה: 17:00
                </p>
                <div class="c-families mt-4" dir="ltr">
                  <div><p>הורי החתן</p><p class="font-semibold">[Familia 1]</p></div>
                  <div><p>הורי הכלה</p><p class="font-semibold">[Familia 2]</p></div>
                </div>
                <p class="c-flip-hint" dir="ltr">← Tocá para ver en español</p>
                <div class="c-spacer"></div>
              </div>
            </div>
          </div>
        </div>

        <!-- ── ENVELOPE (fills stage, always visible) ── -->
        <div class="env-box" :class="{ 'is-open': stage !== 'closed' }">
          <div class="env-back"></div>
          <div class="env-liner"></div>
          <div class="env-flap"></div>
          <div class="env-fold env-fold-left"></div>
          <div class="env-fold env-fold-right"></div>
          <div class="env-fold env-fold-bottom"></div>
          <Transition name="fade">
            <div v-if="stage === 'closed'" class="env-names">
              <span>FAMILIA [NOMBRE 1]</span>
              <span>FAMILIA [NOMBRE 2]</span>
            </div>
          </Transition>
          <Transition name="fade">
            <div v-if="stage === 'closed'" class="env-click" @click="openEnvelope"></div>
          </Transition>
        </div>

      </div><!-- /env-stage -->

      <!-- Hints -->
      <Transition name="fade">
        <p v-if="stage === 'closed'"
          class="mt-5 text-[#8b7355] text-[11px] tracking-[0.3em] uppercase animate-pulse cursor-pointer"
          @click="openEnvelope"
        >Tocá para abrir</p>
      </Transition>

      <Transition name="fade">
        <button v-if="stage === 'card' || stage === 'flipped'"
          class="mt-8 flex flex-col items-center gap-2 text-[#8b7355] hover:text-[#5a4030] transition-colors"
          @click="scrollDown"
        >
          <span class="text-[11px] tracking-[0.3em] uppercase">Ver la invitación</span>
          <svg class="w-5 h-5 animate-bounce" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7"/>
          </svg>
        </button>
      </Transition>

    </div>
  </section>
</template>

<style scoped>

/* ── ENV-STAGE ──────────────────────────────────────────
   Only the envelope height matters for flex layout.
   The card is absolutely positioned inside → doesn't push
   the stage down → envelope stays centered in viewport.
   overflow: visible lets the card extend upward freely.
*/
.env-stage {
  position: relative;
  width: 100%;
  max-width: 460px;
  height: var(--env-h);
  --env-h: 170px;
  overflow: visible;
  /* push envelope slightly below center so the risen card fits above */
  margin-top: 60px;
}
@media (min-width: 480px) { .env-stage { --env-h: 200px; } }
@media (min-width: 640px) { .env-stage { --env-h: 230px; } }


/* ── CARD SLOT ──────────────────────────────────────────
   Absolute inside stage, bottom anchored so the card's
   bottom --overlap sits inside the envelope pocket.
   transform-style: preserve-3d keeps the flip working.
*/
.card-slot {
  position: absolute;
  left: 0; right: 0;
  bottom: var(--overlap);
  --overlap: 40px;
  transform-style: preserve-3d;
}

.card-hidden {
  transform: translateY(340px) scale(0.95);
  opacity: 0;
  pointer-events: none;
}

/*
  Emerge animation:
    0–8%   card inside envelope (invisible)
    8%     just barely peeking above opening → fade in starts
    32%    fully visible, rising nicely
    55%    peak: above envelope
    70%    scale forward ("comes toward viewer")
    100%   settles with --overlap px inside envelope pocket
*/
.card-risen {
  animation: card-emerge 3.4s cubic-bezier(0.25, 0.46, 0.45, 0.94) 0.3s both;
}

@keyframes card-emerge {
  /*
    Opacity:
      0–26%  card inside envelope, invisible
      26%    card top reaches envelope opening → start fade-in
      42%    fully visible while rising
  */
  0%   { transform: translateY(340px) scale(0.95); opacity: 0; }
  26%  { opacity: 0; }
  42%  { opacity: 1; }
  55%  { transform: translateY(-24px) scale(1.0);  opacity: 1; }
  70%  { transform: translateY(-24px) scale(1.06);
         filter: drop-shadow(0 22px 46px rgba(0,0,0,0.19)); }
  100% { transform: translateY(45px)  scale(1.0);  opacity: 1;
         filter: drop-shadow(0 10px 24px rgba(0,0,0,0.13)); }
}


/* ── CARD PERSPECTIVE + FLIPPER ── */
.card-perspective {
  width: 100%;
  perspective: 1400px;
}
.card-flipper {
  width: 100%;
  transform-style: preserve-3d;
  transition: transform 0.85s cubic-bezier(0.4, 0, 0.2, 1);
  cursor: pointer;
  position: relative;
}
.card-flipper.is-flipped { transform: rotateY(180deg); }


/* ── CARD FACE ── */
.card-face {
  width: 100%;
  padding: 1.2rem 1.4rem 0;
  background: #fdfaf6;
  border: 1.5px solid #c9a96e;
  border-radius: 3px;
  box-shadow: 0 6px 28px rgba(0,0,0,0.12);
  backface-visibility: hidden;
  -webkit-backface-visibility: hidden;
  position: relative;
}
.card-face::before {
  content: '';
  position: absolute;
  inset: 10px;
  border: 1px solid rgba(201,169,110,0.28);
  pointer-events: none;
}
.card-face.back {
  position: absolute;
  top: 0; width: 100%;
  transform: rotateY(180deg);
}

/* Empty spacer at card bottom — this is what sits inside the envelope */
.c-spacer { height: var(--overlap, 40px); }


/* ── CARD TYPOGRAPHY ── */
.c-bh {
  text-align: center;
  font-family: 'Playfair Display', serif;
  font-size: 0.78rem; color: #8b5e3c;
  margin-bottom: 0.7rem; letter-spacing: 0.06em;
}
.c-intro {
  text-align: center;
  font-family: 'Montserrat', sans-serif;
  font-size: 0.63rem; color: #5a4030; line-height: 1.6;
  margin-bottom: 0.5rem;
}
.c-names {
  text-align: center;
  font-family: 'Great Vibes', cursive;
  font-size: 2rem; color: #8b5e3c; line-height: 1.1;
  margin: 0.1rem 0;
}
.c-names span {
  font-family: 'Playfair Display', serif;
  font-size: 1rem; vertical-align: middle; margin: 0 0.1rem;
}
.c-rule { width: 40px; height: 1px; background: #c9a96e; margin: 0.5rem auto; }
.c-detail {
  text-align: center;
  font-family: 'Montserrat', sans-serif;
  font-size: 0.63rem; color: #5a4030; line-height: 1.65;
}
.c-families {
  display: flex; justify-content: space-around;
  margin-top: 0.6rem; padding-top: 0.55rem;
  border-top: 1px solid rgba(201,169,110,0.28);
  font-family: 'Montserrat', sans-serif;
  font-size: 0.58rem; color: #5a4030; text-align: center; line-height: 1.45;
}
.c-flip-hint {
  text-align: center;
  font-family: 'Montserrat', sans-serif;
  font-size: 0.52rem; color: #b8a082; margin-top: 0.45rem; letter-spacing: 0.04em;
}


/* ── ENVELOPE BOX (fills the stage) ── */
.env-box {
  position: absolute;
  inset: 0;
  z-index: 2;
}
.env-back {
  position: absolute; inset: 0;
  background: #ede8df; border-radius: 3px;
  box-shadow: 0 8px 36px rgba(0,0,0,0.13), 0 2px 6px rgba(0,0,0,0.06);
  z-index: 1;
}
.env-liner {
  position: absolute; inset: 0;
  background: linear-gradient(155deg,#d4bf90 0%,#eedfa8 40%,#c4a45a 70%,#dfc47a 100%);
  clip-path: polygon(0 0,100% 0,50% 52%);
  z-index: 2; opacity: 0;
  transition: opacity .7s ease .2s;
}
.is-open .env-liner { opacity: 1; }

.env-flap {
  position: absolute; inset: 0;
  background: #e5ddd0;
  clip-path: polygon(0 0,100% 0,50% 52%);
  transform-origin: top center;
  transform: perspective(900px) rotateX(0deg);
  transition: transform 1s cubic-bezier(.4,0,.2,1);
  z-index: 4;
  backface-visibility: hidden; -webkit-backface-visibility: hidden;
}
.is-open .env-flap { transform: perspective(900px) rotateX(-178deg); }

.env-fold            { position: absolute; inset: 0; z-index: 3; }
.env-fold-left       { background: #e0d8cc; clip-path: polygon(0 0,50% 52%,0 100%); }
.env-fold-right      { background: #e0d8cc; clip-path: polygon(100% 0,50% 52%,100% 100%); }
.env-fold-bottom     { background: #d9d0c2; clip-path: polygon(0 100%,100% 100%,50% 52%); }

.env-names {
  position: absolute; inset: 0; z-index: 5;
  display: flex; align-items: flex-end; justify-content: space-between;
  padding: 0 10% 18%;
  font-family: 'Playfair Display', serif;
  font-size: 0.56rem; letter-spacing: .13em; color: #6b5545;
  pointer-events: none;
}
@media (min-width: 480px) { .env-names { font-size: 0.68rem; } }

.env-click { position: absolute; inset: 0; z-index: 6; cursor: pointer; }


/* ── TRANSITIONS ── */
.fade-enter-active, .fade-leave-active { transition: opacity .4s ease; }
.fade-enter-from,  .fade-leave-to      { opacity: 0; }
</style>
