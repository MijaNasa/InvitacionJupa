<template>
  <section id="main-content" class="main-section">

    <!-- Separador decorativo -->
    <div class="divider-top">
      <span class="divider-line"></span>
      <span class="divider-icon">✦</span>
      <span class="divider-line"></span>
    </div>

    <!-- Bienvenida -->
    <div class="block welcome">
      <p class="label">Domingo 16 de Agosto · 2026</p>
      <h2 class="title">¡Los esperamos!</h2>
      <p class="subtitle">
        Será un honor compartir este momento<br>
        tan especial con ustedes
      </p>
      <div class="gold-rule"></div>
      <p class="times">
        <span>Kabalat Panim <strong>16:00 hs</strong></span>
        <span class="dot">·</span>
        <span>Jupá <strong>17:00 hs</strong></span>
      </p>
    </div>

    <!-- Cards -->
    <div class="cards">

      <!-- Dress code -->
      <div class="card">
       
        <h3 class="card-title">Dress code</h3>
        <p class="card-body2">
          Agradecemos asistir con recato
        </p>
      </div>

      <!-- Cómo llegar -->
      <div class="card">
       
        <h3 class="card-title">Cómo llegar</h3>
        <p class="card-body">
          Salón Estancia Pizarro<br>
          <em>Av Ejército Argentino 47</em><br>
          La Calera Córdoba
        </p>
        <a
          href="https://maps.app.goo.gl/amPtS31tGbpbLRVV9?g_st=iw"
          target="_blank"
          rel="noopener"
          class="card-link"
        >Ver en el mapa →</a>
      </div>

    </div>

    <!-- RSVP -->
    <div class="block rsvp">
      <p class="label">Confirmar asistencia</p>
      <p class="rsvp-note">
        Por favor confirmá  tan pronto sea posible
      </p>
      <a
        href="https://forms.gle/faiGHecEcRjTK7TX9"
        target="_blank"
        rel="noopener"
        class="rsvp-btn"
      >
        Completar formulario
      </a>
    </div>

    <!-- Footer -->
    <div class="block footer-msg">
      <img src="/fotoCamiYMija2.png" alt="Cami y Mija" class="couple-photo" />
      <div class="gift-block">
        <p class="gift-msg">Para quienes deseen hacernos un regalo <br>compartimos nuestro alias :</p>
        <p class="alias">jupa.camiymija</p>
      </div>
      <div class="gold-rule"></div>

      <p class="families">Familia Nasatsky · Familia Eblagon</p>
      
    </div>

  </section>
</template>

<style scoped>
.main-section {
  background: #f0ebe2;
  padding: 0 1.5rem 3rem;
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0;
  font-family: 'Atteron', 'Montserrat', sans-serif;
  color: #5a3e2b;
}

/* ── SEPARADOR ── */
.divider-top {
  display: flex;
  align-items: center;
  gap: 12px;
  width: 100%;
  max-width: 360px;
  padding: 1.25rem 0 1rem;
}
.divider-line {
  flex: 1;
  height: 1px;
  background: #c9a96e;
  opacity: 0.4;
}
.divider-icon {
  color: #c9a96e;
  font-size: 10px;
  opacity: 0.7;
}

/* ── BLOQUES GENERALES ── */
.block {
  width: 100%;
  max-width: 360px;
  text-align: center;
  padding: 0 0 1.25rem;
}

.label {
  font-size: 0.6rem;
  letter-spacing: 0.3em;
  text-transform: uppercase;
  color: #c9a96e;
  margin-bottom: 0.75rem;
}

.title {
  font-family: 'Atteron', 'Playfair Display', serif;
  font-size: 2rem;
  font-weight: 400;
  color: #3d2b1a;
  margin: 0 0 0.75rem;
  line-height: 1.2;
}

.subtitle {
  font-size: 0.78rem;
  line-height: 1.8;
  color: #7a5c42;
  margin-bottom: 0.75rem;
}

.gold-rule {
  width: 40px;
  height: 1px;
  background: #c9a96e;
  opacity: 0.5;
  margin: 0 auto 1.25rem;
}

.times {
  font-size: 0.72rem;
  letter-spacing: 0.08em;
  color: #7a5c42;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 10px;
}
.times strong { color: #3d2b1a; font-weight: 600; }
.dot { color: #c9a96e; }

/* ── CARDS ── */
.cards {
  display: flex;
  flex-direction: row;
  gap: 0.6rem;
  width: 100%;
  max-width: 360px;
  margin-bottom: 1.25rem;
}

.card {
  background: #fdfaf6;
  flex: 1;
  border: 1px solid #e2d5c0;
  border-radius: 6px;
  padding: 1rem 1.25rem;
  text-align: center;
  box-shadow: 0 2px 10px rgba(80, 60, 40, 0.06);
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.3rem;
}
.card-icon {
  font-size: 1.1rem;
}
.card-title {
  font-family: 'Atteron', 'Playfair Display', serif;
  font-size: 1.1rem;
  font-weight: 400;
  color: #3d2b1a;
  margin: 0;
  letter-spacing: 0.03em;
}
.card-body {
  font-size: 0.62rem;
  line-height: 1.7;
  color: #7a5c42;
  margin: 0;
}
.card-body2 {
  font-size: 0.72rem;
  line-height: 1.7;
  color: #7a5c42;
  margin-top: 10px;
}
.card-body strong { color: #3d2b1a; }
.card-body em { font-style: normal; color: #c9a96e; }
.card-link {
  display: inline-block;
  font-size: 0.68rem;
  letter-spacing: 0.15em;
  text-transform: uppercase;
  color: #c9a96e;
  text-decoration: none;
  border-bottom: 1px solid rgba(201,169,110,0.4);
  padding-bottom: 1px;
  transition: opacity 0.2s;
}
.card-link:hover { opacity: 0.7; }

/* ── RSVP ── */
.rsvp { padding-bottom: 2.5rem; }

.rsvp-note {
  font-size: 0.76rem;
  color: #7a5c42;
  margin-bottom: 1.5rem;
  line-height: 1.6;
}
.rsvp-note strong { color: #3d2b1a; }

.rsvp-btn {
  display: inline-block;
  background: #3d2b1a;
  color: #f5f0e8;
  font-family: 'Atteron', 'Montserrat', sans-serif;
  font-size: 0.7rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  text-decoration: none;
  padding: 0.9rem 2rem;
  border-radius: 2px;
  transition: background 0.2s, transform 0.15s;
}
.rsvp-btn:hover {
  background: #5a3e2b;
  transform: translateY(-1px);
}

/* ── FOOTER MSG ── */
.footer-msg { padding-top: 1rem; }

.couple-photo {
  width: 100%;
  max-width: 280px;
  aspect-ratio: 3 / 4;
  object-fit: cover;
  border-radius: 4px;
  display: block;
  margin: 0 auto 1.5rem;
  box-shadow: 0 6px 24px rgba(80, 60, 40, 0.14);
}

.hebrew-footer {
  font-family: 'Playfair Display', serif;
  font-size: 1rem;
  color: #c9a96e;
  margin-bottom: 0.5rem;
  letter-spacing: 0.05em;
}

.families {
  font-size: 0.65rem;
  letter-spacing: 0.2em;
  text-transform: uppercase;
  color: #a08060;
  margin-bottom: 0.4rem;
}

.gift-block {
  margin: 0 auto 1rem;
  padding: 0.6rem 0.9rem;
  border: 1px solid #e2d5c0;
  border-radius: 6px;
  background: #fdfaf6;
  max-width: 280px;
  box-shadow: 0 2px 10px rgba(80, 60, 40, 0.06);
}

.gift-msg {
  font-family: 'Atteron', serif;
  font-size: 0.62rem;
  letter-spacing: 0.08em;
  color: #7a5c42;
  line-height: 1.7;
  margin: 0 0 0.6rem;
}

.alias {
  font-family: 'Montserrat', sans-serif;
  font-size: 0.7rem;
  font-weight: 600;
  letter-spacing: 0.12em;
  color: #c9a96e;
  margin: 0;
}

</style>
