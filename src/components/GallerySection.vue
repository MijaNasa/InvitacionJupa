<script setup>
</script>

<template>
  <section class="py-20 px-4">
    <div class="max-w-xl mx-auto text-center space-y-12">
        <!-- Romantic Quote -->
        <p class="font-elegant text-3xl md:text-5xl leading-relaxed text-[#a95c2a] px-4 italic">
            " אני לדודי ודודי לי"
        </p>

        <!-- Decorative Illustration -->
        <div class="flex justify-center py-4">
             <img 
                src="/wedding_rings_icon_1773595186699.png" 
                alt="Alianzas" 
                class="w-16 h-auto opacity-50"
            />
        </div>

        <!-- Single Couple Photo -->
        <div class="flex justify-center px-4">
            <div class="w-full max-w-md overflow-hidden rounded-2xl shadow-xl ring-8 ring-white/50 transition-transform duration-500 hover:scale-[1.01]">
                <img src="/foto_pareja.jpg" class="w-full h-auto object-cover" alt="Cami y Mija" />
            </div>
        </div>

        <!-- Back to Top Button style footer decoration -->
        <div class="pt-8">
            <button class="w-10 h-10 rounded-full border border-[#b9ccdc] flex items-center justify-center text-[#c5bd63] hover:bg-[#a95c2a] hover:text-white transition-colors mx-auto">
                <svg xmlns="http://www.w3.org/2000/svg" class="h-6 w-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                    <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M5 15l7-7 7 7" />
                </svg>
            </button>
        </div>
    </div>
  </section>
</template>
