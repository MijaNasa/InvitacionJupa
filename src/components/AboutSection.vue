<template>
  <section id="about" class="bg-[#f5f4f0]">
    <div class="max-w-7xl mx-auto px-6 py-24">
      <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 items-start">
        
        <!-- Left: Text content -->
        <div>
          <p class="font-body text-brand-green text-xs uppercase tracking-[0.3em] mb-4">/ Sobre Nosotros</p>
          <h2 class="font-heading text-[#111] text-4xl md:text-5xl uppercase leading-[0.9] mb-8">
            METALURGIA DE<br/>
            <span class="text-brand-green">PRECISIÓN</span> DESDE<br/>
            MÁS DE 20 AÑOS
          </h2>
          
          <div class="space-y-4 font-body text-[#111]/60 text-base leading-relaxed">
            <p>
              <strong class="text-brand-green font-bold">Metalúrgica Eblagon</strong> es una empresa familiar con más de 20 años de experiencia, dedicada a la fabricación y trabajos a pedido.
            </p>
            <p>
              Nuestra prioridad es ofrecer calidad, cumplimiento y confianza en cada trabajo. Contamos con tecnología de vanguardia y un equipo altamente calificado para brindar resultados excepcionales.
            </p>
            <p>
              Trabajamos con tornos y centros de mecanizado CNC, atendiendo a clientes que exigen los más altos estándares de precisión y confiabilidad.
            </p>
          </div>
        </div>

        <!-- Right: Stats & circular worker images -->
        <div class="flex flex-col gap-8">
          <!-- Worker circles stacked -->
          <div class="flex flex-col items-center gap-3">
            <div class="flex gap-3 justify-center">
              <div class="w-28 h-28 rounded-full overflow-hidden border-4 border-brand-green/40 shadow-[0_0_20px_rgba(29,94,65,0.3)]">
                <img src="/proyecto-1.png" alt="Operario 1" class="w-full h-full object-cover" />
              </div>
              <div class="w-28 h-28 rounded-full overflow-hidden border-4 border-brand-green/40 shadow-[0_0_20px_rgba(29,94,65,0.3)] mt-6">
                <img src="/proyecto-2.png" alt="Operario 2" class="w-full h-full object-cover" />
              </div>
              <div class="w-28 h-28 rounded-full overflow-hidden border-4 border-brand-green/40 shadow-[0_0_20px_rgba(29,94,65,0.3)]">
                <img src="/proyecto-3.png" alt="Operario 3" class="w-full h-full object-cover" />
              </div>
            </div>
            <div class="text-center mt-2">
              <div class="font-heading text-[#111] text-2xl">20+ Años</div>
              <div class="font-heading text-brand-green text-xl">de Trayectoria</div>
              <div class="font-body text-[#111]/40 text-xs mt-1">• Empresa Familiar</div>
            </div>
          </div>

          <!-- Stats Grid -->
          <div class="grid grid-cols-2 gap-4 border-t border-[#111]/10 pt-6">
            <div class="bg-white rounded-xl p-5 shadow-sm">
              <div class="font-heading text-brand-green text-3xl mb-1">20+</div>
              <div class="font-body text-[#111]/50 text-xs uppercase tracking-wider">Años de Trayectoria</div>
            </div>
            <div class="bg-white rounded-xl p-5 shadow-sm">
              <div class="font-heading text-brand-green text-3xl mb-1">5K+</div>
              <div class="font-body text-[#111]/50 text-xs uppercase tracking-wider">Proyectos Entregados</div>
            </div>
            <div class="bg-white rounded-xl p-5 shadow-sm">
              <div class="font-heading text-brand-green text-3xl mb-1">50</div>
              <div class="font-body text-[#111]/50 text-xs uppercase tracking-wider">Profesionales</div>
            </div>
            <div class="bg-white rounded-xl p-5 shadow-sm">
              <div class="font-heading text-brand-green text-3xl mb-1">100%</div>
              <div class="font-body text-[#111]/50 text-xs uppercase tracking-wider">Satisfacción del Cliente</div>
            </div>
          </div>
        </div>

      </div>
    </div>
  </section>
</template>
