<template>
  <section id="why-us" class="relative bg-[#f5f4f0] overflow-hidden">
    <!-- Background with industrial image overlay -->
    <div class="absolute inset-0 bg-cover bg-center bg-no-repeat opacity-20" style="background-image: url('/hero-bg.png');"></div>
    <div class="absolute inset-0 bg-gradient-to-r from-black via-black/80 to-black/60"></div>

    <div class="relative z-10 max-w-7xl mx-auto px-6 py-24">
      <!-- Header -->
      <div class="mb-16">
        <p class="font-body text-brand-green text-xs uppercase tracking-[0.3em] mb-4">Por qué Elegirnos</p>
        <div class="flex items-baseline gap-4">
          <span class="font-heading text-brand-green/20 text-[120px] leading-none select-none">05</span>
          <h2 class="font-heading text-white text-4xl md:text-6xl uppercase leading-tight">
            RAZONES
          </h2>
        </div>
      </div>

      <!-- Cards Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-5">

        <!-- Card 1 -->
        <div class="group bg-white/5 border border-white/10 hover:border-brand-green/40 rounded-2xl p-8 transition-all duration-300 hover:-translate-y-1">
          <div class="w-12 h-12 rounded-xl bg-brand-green/10 group-hover:bg-brand-green/20 flex items-center justify-center mb-5">
            <svg class="w-6 h-6 text-brand-green" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
              <path stroke-linecap="round" stroke-linejoin="round" d="M9 12.75L11.25 15 15 9.75M21 12a9 9 0 11-18 0 9 9 0 0118 0z"/>
            </svg>
          </div>
          <h3 class="font-heading text-white text-xl uppercase mb-3 group-hover:text-brand-green transition-colors">Calidad y Cumplimiento</h3>
          <p class="font-body text-white/50 text-sm leading-relaxed">Nuestro compromiso innegociable con la calidad y los tiempos de entrega acordados.</p>
        </div>

        <!-- Card 2 -->
        <div class="group bg-white/5 border border-white/10 hover:border-brand-green/40 rounded-2xl p-8 transition-all duration-300 hover:-translate-y-1">
          <div class="w-12 h-12 rounded-xl bg-brand-green/10 group-hover:bg-brand-green/20 flex items-center justify-center mb-5">
            <svg class="w-6 h-6 text-brand-green" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
              <path stroke-linecap="round" stroke-linejoin="round" d="M11.42 15.17L17.25 21A2.652 2.652 0 0021 17.25l-5.877-5.877M11.42 15.17l2.496-3.03c.317-.384.74-.626 1.208-.766M11.42 15.17l-4.655 5.653a2.548 2.548 0 11-3.586-3.586l6.837-5.63m5.108-.233c.55-.164 1.163-.188 1.743-.14a4.5 4.5 0 004.486-6.336l-3.276 3.277a3.004 3.004 0 01-2.25-2.25l3.276-3.276a4.5 4.5 0 00-6.336 4.486c.091 1.076-.071 2.264-.904 2.95l-.102.085m-1.745 1.437L5.909 7.5H4.5L2.25 3.75l1.5-1.5L7.5 4.5v1.409l4.26 4.26m-1.745 1.437l1.745-1.437m6.615 8.206L15.75 15.75M4.867 19.125h.008v.008h-.008v-.008z"/>
            </svg>
          </div>
          <h3 class="font-heading text-white text-xl uppercase mb-3 group-hover:text-brand-green transition-colors">Experiencia en Mecanizado</h3>
          <p class="font-body text-white/50 text-sm leading-relaxed">Más de tres décadas dominando técnicas avanzadas de mecanizado industrial.</p>
        </div>

        <!-- Card 3 -->
        <div class="group bg-white/5 border border-white/10 hover:border-brand-green/40 rounded-2xl p-8 transition-all duration-300 hover:-translate-y-1">
          <div class="w-12 h-12 rounded-xl bg-brand-green/10 group-hover:bg-brand-green/20 flex items-center justify-center mb-5">
            <svg class="w-6 h-6 text-brand-green" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
              <path stroke-linecap="round" stroke-linejoin="round" d="M9.594 3.94c.09-.542.56-.94 1.11-.94h2.593c.55 0 1.02.398 1.11.94l.213 1.281c.063.374.313.686.645.87.074.04.147.083.22.127.324.196.72.257 1.075.124l1.217-.456a1.125 1.125 0 011.37.49l1.296 2.247a1.125 1.125 0 01-.26 1.431l-1.003.827c-.293.24-.438.613-.431.992a6.759 6.759 0 010 .255c-.007.378.138.75.43.99l1.005.828c.424.35.534.954.26 1.43l-1.298 2.247a1.125 1.125 0 01-1.369.491l-1.217-.456c-.355-.133-.75-.072-1.076.124a6.57 6.57 0 01-.22.128c-.331.183-.581.495-.644.869l-.213 1.28c-.09.543-.56.941-1.11.941h-2.594c-.55 0-1.02-.398-1.11-.94l-.213-1.281c-.062-.374-.312-.686-.644-.87a6.52 6.52 0 01-.22-.127c-.325-.196-.72-.257-1.076-.124l-1.217.456a1.125 1.125 0 01-1.369-.49l-1.297-2.247a1.125 1.125 0 01.26-1.431l1.004-.827c.292-.24.437-.613.43-.992a6.932 6.932 0 010-.255c.007-.378-.138-.75-.43-.99l-1.004-.828a1.125 1.125 0 01-.26-1.43l1.297-2.247a1.125 1.125 0 011.37-.491l1.216.456c.356.133.751.072 1.076-.124.072-.044.146-.087.22-.128.332-.183.582-.495.644-.869l.214-1.281z"/>
            </svg>
          </div>
          <h3 class="font-heading text-white text-xl uppercase mb-3 group-hover:text-brand-green transition-colors">Trabajos a Pedido</h3>
          <p class="font-body text-white/50 text-sm leading-relaxed">Fabricamos piezas personalizadas según sus requerimientos específicos y materiales de alta calidad.</p>
        </div>

        <!-- Card 4 -->
        <div class="group bg-white/5 border border-white/10 hover:border-brand-green/40 rounded-2xl p-8 transition-all duration-300 hover:-translate-y-1">
          <div class="w-12 h-12 rounded-xl bg-brand-green/10 group-hover:bg-brand-green/20 flex items-center justify-center mb-5">
            <svg class="w-6 h-6 text-brand-green" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5">
              <path stroke-linecap="round" stroke-linejoin="round" d="M15 19.128a9.38 9.38 0 002.625.372 9.337 9.337 0 004.121-.952 4.125 4.125 0 00-7.533-2.493M15 19.128v-.003c0-1.113-.285-2.16-.786-3.07M15 19.128v.106A12.318 12.318 0 018.624 21c-2.331 0-4.512-.645-6.374-1.766l-.001-.109a6.375 6.375 0 0111.964-3.07M12 6.375a3.375 3.375 0 11-6.75 0 3.375 3.375 0 016.75 0zm8.25 2.25a2.625 2.625 0 11-5.25 0 2.625 2.625 0 015.25 0z"/>
            </svg>
          </div>
          <h3 class="font-heading text-white text-xl uppercase mb-3 group-hover:text-brand-green transition-colors">Asesoramiento Sincero</h3>
          <p class="font-body text-white/50 text-sm leading-relaxed">Atención directa y asesoramiento técnico honesto para optimizar sus proyectos.</p>
        </div>

      </div>
    </div>
  </section>
</template>
