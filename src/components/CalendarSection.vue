<script setup>
</script>

<template>
  <section class="py-20 px-6 border-t border-wedding-accent/10">
    <div class="section-container space-y-8">
        <!-- Calendar Icon -->
        <div class="flex justify-center">
            <div class="w-20 h-20 rounded-2xl border-2 border-wedding-blue flex flex-col overflow-hidden shadow-sm">
                <div class="bg-wedding-blue h-6"></div>
                <div class="flex-1 flex items-center justify-center">
                    <svg xmlns="http://www.w3.org/2000/svg" class="h-10 w-10 text-wedding-blue" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                        <path stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5" d="M4.318 6.318a4.5 4.5 0 000 6.364L12 20.364l7.682-7.682a4.5 4.5 0 00-6.364-6.364L12 7.636l-1.318-1.318a4.5 4.5 0 00-6.364 0z" />
                    </svg>
                </div>
            </div>
        </div>

        <p class="text-wedding-blue/80 font-medium italic">
            ¡Agendá la fecha en tu calendario!
        </p>

        <button class="btn-wedding bg-[#6b7280] flex items-center gap-2 mx-auto">
            Agendar Evento
            <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" fill="none" viewBox="0 0 24 24" stroke="currentColor">
                <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 9l-7 7-7-7" />
            </svg>
        </button>

        <div class="pt-20 opacity-20 flex justify-center scale-x-[-1]">
             <img src="/wedding_decorative_flowers_blue_1773595204314.png" class="w-48 h-auto" />
        </div>
    </div>
  </section>
</template>
