<script setup>
import { ref } from 'vue';

const form = ref({
  nombre: '',
  empresa: '',
  email: '',
  telefono: '',
  mensaje: ''
});

const handleSubmit = (e) => {
  e.preventDefault();
  alert('¡Gracias por su mensaje! Nos pondremos en contacto a la brevedad.');
  form.value = { nombre: '', empresa: '', email: '', telefono: '', mensaje: '' };
};
</script>

<template>
  <section id="contact" class="bg-[#060606]">
    <div class="max-w-7xl mx-auto px-6 py-24">
      <!-- Header -->
      <div class="mb-14">
        <p class="font-body text-brand-green text-xs uppercase tracking-[0.3em] mb-4">Contacto</p>
        <h2 class="font-heading text-white text-4xl md:text-6xl uppercase leading-[0.9]">
          Consultanos por tu proyecto
        </h2>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-2 gap-16">
        <!-- Left: info -->
        <div class="flex flex-col justify-between">
          <div>
            <p class="font-body text-white/50 text-base leading-relaxed mb-10 max-w-md">
              Si necesitás fabricar una pieza, cuchillas para cortadora de fiambre o realizar un trabajo metalúrgico específico, podemos ayudarte. Contactanos y contanos qué necesitás. <br/><br/>
              <strong>¡Realizamos envíos a todo el país!</strong>
            </p>

            <div class="space-y-5 mb-10">
              <div class="flex items-center gap-4 group">
                <div class="w-10 h-10 rounded-full bg-brand-green/10 flex items-center justify-center shrink-0 group-hover:bg-brand-green/20 transition-all">
                  <svg class="w-4 h-4 text-brand-green" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5"><path stroke-linecap="round" stroke-linejoin="round" d="M15 10.5a3 3 0 11-6 0 3 3 0 016 0z"/><path stroke-linecap="round" stroke-linejoin="round" d="M19.5 10.5c0 7.142-7.5 11.25-7.5 11.25S4.5 17.642 4.5 10.5a7.5 7.5 0 1115 0z"/></svg>
                </div>
                <div class="flex flex-col">
                  <span class="font-body text-white/50 text-sm">Av Juan B. Justo 7946, Córdoba</span>
                  <span class="font-body text-white/20 text-xs">CP: 5000</span>
                </div>
              </div>
              <div class="flex items-center gap-4 group">
                <div class="w-10 h-10 rounded-full bg-brand-green/10 flex items-center justify-center shrink-0 group-hover:bg-brand-green/20 transition-all">
                  <svg class="w-4 h-4 text-brand-green" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5"><path stroke-linecap="round" stroke-linejoin="round" d="M2.25 6.75c0 8.284 6.716 15 15 15h2.25a2.25 2.25 0 002.25-2.25v-1.372c0-.516-.351-.966-.852-1.091l-4.423-1.106c-.44-.11-.902.055-1.173.417l-.97 1.293c-.282.376-.769.542-1.21.38a12.035 12.035 0 01-7.143-7.143c-.162-.441.004-.928.38-1.21l1.293-.97c.363-.271.527-.734.417-1.173L6.963 3.102a1.125 1.125 0 00-1.091-.852H4.5A2.25 2.25 0 002.25 4.5v2.25z"/></svg>
                </div>
                <span class="font-body text-white/50 text-sm">351 681 5340</span>
              </div>
              <div class="flex items-center gap-4 group">
                <div class="w-10 h-10 rounded-full bg-brand-green/10 flex items-center justify-center shrink-0 group-hover:bg-brand-green/20 transition-all">
                  <svg class="w-4 h-4 text-brand-green" fill="none" viewBox="0 0 24 24" stroke="currentColor" stroke-width="1.5"><path stroke-linecap="round" stroke-linejoin="round" d="M21.75 6.75v10.5a2.25 2.25 0 01-2.25 2.25h-15a2.25 2.25 0 01-2.25-2.25V6.75m19.5 0A2.25 2.25 0 0019.5 4.5h-15a2.25 2.25 0 00-2.25 2.25m19.5 0v.243a2.25 2.25 0 01-1.07 1.916l-7.5 4.615a2.25 2.25 0 01-2.36 0L3.32 8.91a2.25 2.25 0 01-1.07-1.916V6.75"/></svg>
                </div>
                <span class="font-body text-white/50 text-sm">Matieblagon18@gmail.com</span>
              </div>
            </div>
          </div>

          <!-- WhatsApp -->
          <a 
            href="https://wa.me/543516815340" 
            target="_blank" 
            rel="noopener noreferrer" 
            class="inline-flex items-center gap-3 bg-[#25D366] hover:bg-[#128C7E] text-white font-heading text-sm uppercase tracking-widest px-8 py-4 rounded-full transition-all duration-300 shadow-[0_0_20px_rgba(37,211,102,0.3)] hover:shadow-[0_0_30px_rgba(37,211,102,0.5)] w-fit"
          >
            <svg viewBox="0 0 24 24" class="w-5 h-5 fill-current"><path d="M17.472 14.382c-.297-.149-1.758-.867-2.03-.967-.273-.099-.471-.148-.67.15-.197.297-.767.966-.94 1.164-.173.199-.347.223-.644.075-.297-.15-1.255-.463-2.39-1.475-.883-.788-1.48-1.761-1.653-2.059-.173-.297-.018-.458.13-.606.134-.133.298-.347.446-.52.149-.174.198-.298.298-.497.099-.198.05-.371-.025-.52-.075-.149-.669-1.612-.916-2.207-.242-.579-.487-.5-.669-.51a12.8 12.8 0 0 0-.57-.01c-.198 0-.52.074-.792.372-.272.297-1.04 1.016-1.04 2.479 0 1.462 1.065 2.875 1.213 3.074.149.198 2.096 3.2 5.077 4.487.709.306 1.262.489 1.694.625.712.227 1.36.195 1.871.118.571-.085 1.758-.719 2.006-1.413.248-.694.248-1.289.173-1.413-.074-.124-.272-.198-.57-.347m-5.421 7.403h-.004a9.87 9.87 0 0 1-5.031-1.378l-.361-.214-3.741.982.998-3.648-.235-.374a9.86 9.86 0 0 1-1.51-5.26c.001-5.45 4.436-9.884 9.888-9.884 2.64 0 5.122 1.03 6.988 2.898a9.825 9.825 0 0 1 2.893 6.994c-.003 5.45-4.437 9.884-9.885 9.884m8.413-18.297A11.815 11.815 0 0 0 12.05 0C5.495 0 .16 5.335.157 11.892c0 2.096.547 4.142 1.588 5.945L.057 24l6.305-1.654a11.882 11.882 0 0 0 5.683 1.448h.005c6.554 0 11.89-5.335 11.893-11.893a11.821 11.821 0 0 0-3.48-8.413Z"/></svg>
            WhatsApp Directo
          </a>
        </div>

        <!-- Right: Form -->
        <div>
          <form @submit="handleSubmit" class="bg-white/5 border border-white/10 rounded-2xl p-8 backdrop-blur-sm">
            <h3 class="font-heading text-white text-2xl uppercase mb-6">Solicitar Presupuesto</h3>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-5 mb-5">
              <div>
                <label for="nombre" class="block font-body text-white/40 text-xs uppercase tracking-wider mb-2">Nombre Completo</label>
                <input type="text" id="nombre" v-model="form.nombre" required
                  class="w-full bg-white/5 border border-white/10 rounded-xl text-white font-body text-sm p-3.5 focus:border-brand-green focus:outline-none focus:ring-1 focus:ring-brand-green/30 transition-all placeholder-white/20"
                  placeholder="Tu nombre"
                />
              </div>
              <div>
                <label for="empresa" class="block font-body text-white/40 text-xs uppercase tracking-wider mb-2">Empresa</label>
                <input type="text" id="empresa" v-model="form.empresa"
                  class="w-full bg-white/5 border border-white/10 rounded-xl text-white font-body text-sm p-3.5 focus:border-brand-green focus:outline-none focus:ring-1 focus:ring-brand-green/30 transition-all placeholder-white/20"
                  placeholder="Nombre de empresa"
                />
              </div>
            </div>

            <div class="grid grid-cols-1 md:grid-cols-2 gap-5 mb-5">
              <div>
                <label for="email" class="block font-body text-white/40 text-xs uppercase tracking-wider mb-2">Correo Electrónico</label>
                <input type="email" id="email" v-model="form.email" required
                  class="w-full bg-white/5 border border-white/10 rounded-xl text-white font-body text-sm p-3.5 focus:border-brand-green focus:outline-none focus:ring-1 focus:ring-brand-green/30 transition-all placeholder-white/20"
                  placeholder="tu@email.com"
                />
              </div>
              <div>
                <label for="telefono" class="block font-body text-white/40 text-xs uppercase tracking-wider mb-2">Teléfono</label>
                <input type="tel" id="telefono" v-model="form.telefono"
                  class="w-full bg-white/5 border border-white/10 rounded-xl text-white font-body text-sm p-3.5 focus:border-brand-green focus:outline-none focus:ring-1 focus:ring-brand-green/30 transition-all placeholder-white/20"
                  placeholder="+54 351 ..."
                />
              </div>
            </div>

            <div class="mb-6">
              <label for="mensaje" class="block font-body text-white/40 text-xs uppercase tracking-wider mb-2">Detalles del Proyecto</label>
              <textarea id="mensaje" v-model="form.mensaje" rows="4" required
                class="w-full bg-white/5 border border-white/10 rounded-xl text-white font-body text-sm p-3.5 focus:border-brand-green focus:outline-none focus:ring-1 focus:ring-brand-green/30 transition-all resize-none placeholder-white/20"
                placeholder="Describí tu proyecto, materiales, dimensiones..."
              ></textarea>
            </div>

            <button type="submit" class="w-full flex items-center justify-center gap-3 bg-brand-green hover:bg-[#164d33] text-white font-heading text-sm uppercase tracking-widest px-8 py-4 rounded-xl transition-all duration-300 shadow-[0_0_20px_rgba(29,94,65,0.4)] hover:shadow-[0_0_40px_rgba(29,94,65,0.6)] hover:scale-[1.02]">
              Enviar Consulta
              <svg class="w-4 h-4" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3"/></svg>
            </button>
          </form>
        </div>
      </div>
    </div>
  </section>
</template>
