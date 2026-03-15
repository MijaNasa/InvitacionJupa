<template>
  <section id="process" class="bg-[#f5f4f0]">
    <div class="max-w-7xl mx-auto px-6 py-24">
      <!-- Header -->
      <div class="text-center mb-16">
        <p class="font-body text-brand-green text-xs uppercase tracking-[0.3em] mb-4">Metodología</p>
        <h2 class="font-heading text-[#111111] text-4xl md:text-6xl uppercase leading-[0.9]">
          NUESTRO <span class="text-brand-green">PROCESO</span>
        </h2>
      </div>

      <!-- Steps -->
      <div class="relative">
        <!-- Connecting line -->
        <div class="hidden lg:block absolute top-10 left-[10%] w-[80%] h-px bg-brand-green/30"></div>

        <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-8">
          <!-- Step 1 -->
          <div class="relative z-10 text-center group">
            <div class="w-20 h-20 mx-auto mb-6 rounded-full font-heading text-3xl flex items-center justify-center transition-all duration-300 bg-brand-green text-white shadow-[0_0_20px_rgba(29,94,65,0.4)]">
              01
            </div>
            <div class="h-px bg-brand-green/30 w-full mb-6 hidden lg:block absolute top-10 -right-1/2"></div>
            <h4 class="font-heading text-[#111] text-lg uppercase mb-3 group-hover:text-brand-green transition-colors">Pedido de Presupuesto</h4>
            <p class="font-body text-[#111]/60 text-sm leading-relaxed">Compartí los requerimientos y especificaciones de tu proyecto con nuestro equipo.</p>
          </div>

          <!-- Step 2 -->
          <div class="relative z-10 text-center group">
            <div class="w-20 h-20 mx-auto mb-6 rounded-full font-heading text-3xl flex items-center justify-center transition-all duration-300 bg-transparent border-2 border-brand-green text-brand-green group-hover:bg-brand-green group-hover:text-white">
              02
            </div>
            <h4 class="font-heading text-[#111] text-lg uppercase mb-3 group-hover:text-brand-green transition-colors">Revisión Técnica</h4>
            <p class="font-body text-[#111]/60 text-sm leading-relaxed">Nuestros ingenieros analizan la factibilidad y proveen recomendaciones técnicas detalladas.</p>
          </div>

          <!-- Step 3 -->
          <div class="relative z-10 text-center group">
            <div class="w-20 h-20 mx-auto mb-6 rounded-full font-heading text-3xl flex items-center justify-center transition-all duration-300 bg-brand-green text-white shadow-[0_0_20px_rgba(29,94,65,0.4)]">
              03
            </div>
            <h4 class="font-heading text-[#111] text-lg uppercase mb-3 group-hover:text-brand-green transition-colors">Fabricación</h4>
            <p class="font-body text-[#111]/60 text-sm leading-relaxed">Manufactura de precisión con maquinaria avanzada y control de calidad riguroso.</p>
          </div>

          <!-- Step 4 -->
          <div class="relative z-10 text-center group">
            <div class="w-20 h-20 mx-auto mb-6 rounded-full font-heading text-3xl flex items-center justify-center transition-all duration-300 bg-transparent border-2 border-brand-green text-brand-green group-hover:bg-brand-green group-hover:text-white">
              04
            </div>
            <h4 class="font-heading text-[#111] text-lg uppercase mb-3 group-hover:text-brand-green transition-colors">Entrega</h4>
            <p class="font-body text-[#111]/60 text-sm leading-relaxed">Entrega a tiempo con documentación completa y soporte técnico post-venta.</p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
