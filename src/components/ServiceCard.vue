<script setup>
defineProps({
  title: String,
  description: String,
  iconSvg: String,
  variant: {
    type: String,
    default: 'dark' // 'dark' | 'green' | 'light'
  }
});
</script>

<template>
  <div
    :class="[
      'group relative rounded-2xl p-7 transition-all duration-300 cursor-default hover:-translate-y-1 hover:shadow-2xl',
      variant === 'green' ? 'bg-brand-green text-white shadow-[0_8px_30px_rgba(29,94,65,0.4)]' :
      variant === 'light' ? 'bg-white/5 border border-white/10 hover:border-brand-green/40' :
      'bg-[#0e0e0e] border border-white/5 hover:border-brand-green/30'
    ]"
  >
    <!-- Icon -->
    <div
      :class="[
        'w-12 h-12 rounded-xl flex items-center justify-center mb-5 transition-all duration-300',
        variant === 'green' ? 'bg-white/20' : 'bg-brand-green/10 group-hover:bg-brand-green/20'
      ]"
    >
      <span v-html="iconSvg" :class="variant === 'green' ? 'text-white' : 'text-brand-green'" class="w-6 h-6"></span>
    </div>

    <!-- Title -->
    <h3
      :class="[
        'font-heading text-xl uppercase mb-3 transition-colors',
        variant === 'green' ? 'text-white' : 'text-white group-hover:text-brand-green'
      ]"
    >
      {{ title }}
    </h3>

    <!-- Description -->
    <p
      :class="[
        'font-body text-sm leading-relaxed',
        variant === 'green' ? 'text-white/80' : 'text-white/50'
      ]"
    >
      {{ description }}
    </p>

    <!-- Learn More link -->
    <div class="mt-5">
      <a
        href="#contact"
        :class="[
          'inline-flex items-center gap-1 font-heading text-xs uppercase tracking-widest transition-colors',
          variant === 'green' ? 'text-white/80 hover:text-white' : 'text-brand-green/60 hover:text-brand-green'
        ]"
      >
        Más Info
        <svg class="w-3 h-3" fill="none" viewBox="0 0 24 24" stroke="currentColor"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14 5l7 7m0 0l-7 7m7-7H3"/></svg>
      </a>
    </div>
  </div>
</template>
