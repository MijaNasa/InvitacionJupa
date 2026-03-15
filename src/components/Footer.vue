<template>
  <footer class="bg-brand-green pt-16 pb-8">
    <div class="max-w-7xl mx-auto px-6">
      <!-- Top grid -->
      <div class="grid grid-cols-1 md:grid-cols-4 gap-12 mb-12">
        <!-- Brand -->
        <div class="md:col-span-1">
        </div>



      </div>

      <!-- Bottom bar -->
      <div class="border-t border-white/20 pt-8 flex flex-col md:flex-row justify-between items-center gap-4">
        <p class="font-body text-white/40 text-xs uppercase tracking-widest">
          © {{ new Date().getFullYear() }} Metalúrgica Eblagon. Todos los derechos reservados.
        </p>
        <div class="flex gap-6 font-body text-white/40 text-xs">
          <a href="#" class="hover:text-white transition-colors">Política de Privacidad</a>
          <a href="#" class="hover:text-white transition-colors">Términos de Servicio</a>
        </div>
      </div>
    </div>
  </footer>
</template>
