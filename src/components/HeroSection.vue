<script setup lang="ts">
import { ref, onMounted } from 'vue'

const visible = ref(false)
onMounted(() => setTimeout(() => { visible.value = true }, 100))

const scrollToWork = () => document.querySelector('#work')?.scrollIntoView({ behavior: 'smooth' })
</script>

<template>
  <section id="hero" class="relative min-h-screen flex flex-col justify-center overflow-hidden pt-24 mesh-hero">
    <!-- Grid lines -->
    <div class="absolute inset-0 grid-bg pointer-events-none" aria-hidden="true" />

    <!-- Rotating rings -->
    <div class="absolute right-0 top-1/2 -translate-y-1/2 translate-x-1/3 opacity-10 pointer-events-none hidden lg:block">
      <svg class="animate-spin-slow" width="600" height="600" viewBox="0 0 600 600" fill="none">
        <circle cx="300" cy="300" r="290" stroke="#c8a96e" stroke-width="1" stroke-dasharray="8 16" />
        <circle cx="300" cy="300" r="220" stroke="#c8a96e" stroke-width="0.5" />
        <circle cx="300" cy="300" r="150" stroke="#c8a96e" stroke-width="1" stroke-dasharray="4 8" />
      </svg>
    </div>

    <div class="relative z-10 max-w-6xl mx-auto px-6 pb-24 w-full">
      <!-- Eyebrow -->
      <div class="hidden-init" :class="visible ? 'animate-fade-up' : ''">
        <span class="section-label">UI / UX Designer</span>
      </div>

      <!-- Headline -->
      <h1
        class="font-display mt-6 leading-none hidden-init"
        :class="visible ? 'animate-fade-up animate-delay-200' : ''"
        style="font-size: clamp(3.5rem, 10vw, 8.5rem); font-weight: 700;"
      >
        <span class="block text-paper">Crafting</span>
        <span class="block italic text-gold">Experiences</span>
        <span class="block text-paper">that Matter</span>
      </h1>

      <!-- Divider -->
      <div class="mt-10 mb-8 hidden-init" :class="visible ? 'animate-fade-up animate-delay-300' : ''">
        <div class="gold-line-h w-60" />
      </div>

      <!-- Bio -->
      <p class="max-w-xl text-lg leading-relaxed text-muted hidden-init" :class="visible ? 'animate-fade-up animate-delay-400' : ''">
        Hi, I'm <span class="text-paper font-medium">Kazi Md. Rakibul Hasan</span> — a product-focused UI/UX designer
        with a passion for turning complex problems into elegant, user-centered solutions.
      </p>

      <!-- CTAs -->
      <div class="mt-10 flex flex-wrap gap-4 items-center hidden-init" :class="visible ? 'animate-fade-up animate-delay-500' : ''">
        <button class="btn-primary" @click="scrollToWork">View Work</button>
        <a href="/rakibul-hasan-cv.pdf" download class="btn-outline">
          <svg width="14" height="14" viewBox="0 0 14 14" fill="none">
            <path d="M7 1v9M4 7l3 4 3-4M1 13h12" stroke="#c8a96e" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
          </svg>
          Download CV
        </a>
      </div>

      <!-- Stats -->
      <div class="mt-16 flex flex-wrap gap-10 hidden-init" :class="visible ? 'animate-fade-up animate-delay-600' : ''">
        <div v-for="[num, label] in [['3+', 'Years Experience'], ['4+', 'Companies'], ['10+', 'Projects']]" :key="num" class="flex flex-col gap-1">
          <span class="font-display text-4xl text-gold font-bold">{{ num }}</span>
          <span class="font-mono text-xs tracking-widest uppercase text-dim">{{ label }}</span>
        </div>
      </div>
    </div>

    <!-- Scroll indicator -->
    <div class="absolute bottom-8 left-1/2 -translate-x-1/2 flex flex-col items-center gap-2 opacity-40">
      <span class="font-mono text-xs tracking-widest uppercase text-dim">Scroll</span>
      <div class="w-px h-12" style="background: linear-gradient(to bottom, #c8a96e, transparent);" />
    </div>
  </section>
</template>
