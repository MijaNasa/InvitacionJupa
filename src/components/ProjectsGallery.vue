<script setup>
const projects = [
  { title: "Cuchillas 330 mm", category: "Producto Principal", image: "/proyecto-1.png" },
  { title: "Cuchillas 325 mm", category: "Producto Principal", image: "/proyecto-2.png" },
  { title: "Cuchillas 300 mm", category: "Producto Principal", image: "/proyecto-3.png" },
  { title: "Mecanizado CNC", category: "Servicios", image: "/proyecto-1.png" },
  { title: "Piezas Especiales", category: "Trabajos a Pedido", image: "/proyecto-2.png" },
  { title: "Medidas especiales", category: "A pedido", image: "/proyecto-3.png" }
];
</script>

<template>
  <section id="projects" class="bg-[#0a0a0a]">
    <div class="max-w-7xl mx-auto px-6 py-24">
      <!-- Header -->
      <div class="flex flex-col md:flex-row justify-between items-end mb-12 gap-6">
        <div>
          <p class="font-body text-brand-green text-xs uppercase tracking-[0.3em] mb-4">Nuestro Portfolio</p>
          <h2 class="font-heading text-white text-4xl md:text-6xl uppercase leading-[0.9]">
            PRODUCTOS <br/>Y SERVICIOS
          </h2>
        </div>
        <p class="font-body text-white/40 text-sm max-w-xs text-right">
          Cuchillas de precisión y soluciones de mecanizado para la industria.
        </p>
      </div>

      <!-- Gallery Grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4">
        <div
          v-for="(item, index) in projects"
          :key="index"
          class="group relative aspect-[4/3] overflow-hidden rounded-2xl cursor-pointer"
        >
          <!-- Image -->
          <img
            :src="item.image"
            :alt="item.title"
            class="absolute inset-0 w-full h-full object-cover transition-transform duration-700 group-hover:scale-110"
          />
          <!-- Dark overlay always -->
          <div class="absolute inset-0 bg-black/40 transition-all duration-300 group-hover:bg-black/20"></div>

          <!-- Hover info slide from bottom -->
          <div class="absolute inset-x-0 bottom-0 bg-gradient-to-t from-black/90 via-black/60 to-transparent translate-y-2 group-hover:translate-y-0 transition-transform duration-500 p-6">
            <span class="font-body text-brand-green text-xs uppercase tracking-widest block mb-1">{{ item.category }}</span>
            <h3 class="font-heading text-white text-xl uppercase">{{ item.title }}</h3>
          </div>
        </div>
      </div>

      <!-- CTA -->
      <div class="text-center mt-12">
        <a href="#contact" class="inline-flex items-center gap-3 bg-brand-green hover:bg-[#164d33] text-white font-heading text-sm uppercase tracking-widest px-10 py-4 rounded-full transition-all duration-300 shadow-[0_0_30px_rgba(29,94,65,0.4)] hover:shadow-[0_0_50px_rgba(29,94,65,0.6)]">
          Iniciar tu Proyecto
          <svg class="w-4 h-4" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3"/></svg>
        </a>
      </div>
    </div>
  </section>
</template>
