<script setup lang="ts">
import { ref, onMounted, onUnmounted } from 'vue'

const scrolled = ref(false)
const menuOpen = ref(false)

const navLinks = [
  { label: 'About', href: '#about' },
  { label: 'Work', href: '#work' },
  { label: 'Skills', href: '#skills' },
  { label: 'Contact', href: '#contact' },
]

const handleScroll = () => { scrolled.value = window.scrollY > 60 }
onMounted(() => window.addEventListener('scroll', handleScroll))
onUnmounted(() => window.removeEventListener('scroll', handleScroll))

const scrollTo = (href: string) => {
  menuOpen.value = false
  document.querySelector(href)?.scrollIntoView({ behavior: 'smooth' })
}
</script>

<template>
  <header class="fixed top-0 left-0 right-0 z-50 transition-all duration-500" :class="scrolled ? 'py-3' : 'py-5'">
    <div
      class="mx-auto max-w-6xl px-6 flex items-center justify-between transition-all duration-500"
      :class="scrolled ? 'bg-ink/90 backdrop-blur-xl border border-gold/10 rounded-2xl py-3.5 px-6' : ''"
    >
      <!-- Logo -->
      <a href="#" class="font-display text-xl font-bold" @click.prevent="scrollTo('#hero')">
        <span class="text-paper">Rakib</span>
      </a>

      <!-- Desktop nav -->
      <nav class="hidden md:flex items-center gap-8">
        <a
          v-for="link in navLinks" :key="link.href"
          :href="link.href"
          class="font-mono text-xs tracking-widest uppercase text-dim hover:text-gold transition-colors duration-300"
          @click.prevent="scrollTo(link.href)"
        >{{ link.label }}</a>
        <a
          href="/rakibul-hasan-cv.pdf" download
          class="flex items-center gap-2 px-5 py-2.5 border border-gold text-gold font-mono text-xs tracking-widest uppercase rounded-full hover:bg-gold hover:text-ink transition-all duration-300"
        >
          <svg width="12" height="12" viewBox="0 0 12 12" fill="none"><path d="M6 1v7M3 5.5l3 3 3-3M1 11h10" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/></svg>
          Download CV
        </a>
      </nav>

      <!-- Mobile hamburger -->
      <button class="md:hidden flex flex-col gap-1.5 p-2" @click="menuOpen = !menuOpen" aria-label="Toggle menu">
        <span class="block w-6 h-0.5 bg-paper transition-all duration-300" :class="menuOpen ? 'rotate-45 translate-y-2' : ''" />
        <span class="block w-6 h-0.5 bg-paper transition-all duration-300" :class="menuOpen ? 'opacity-0' : ''" />
        <span class="block w-6 h-0.5 bg-paper transition-all duration-300" :class="menuOpen ? '-rotate-45 -translate-y-2' : ''" />
      </button>
    </div>

    <!-- Mobile menu -->
    <div
      class="md:hidden absolute top-full left-4 right-4 mt-2 bg-ink/95 backdrop-blur-xl border border-gold/15 rounded-2xl overflow-hidden transition-all duration-300"
      :class="menuOpen ? 'max-h-96 opacity-100' : 'max-h-0 opacity-0'"
    >
      <div class="p-6 flex flex-col gap-5">
        <a v-for="link in navLinks" :key="link.href" :href="link.href"
           class="font-mono text-sm tracking-widest uppercase text-dim hover:text-gold transition-colors"
           @click.prevent="scrollTo(link.href)">{{ link.label }}</a>
        <a href="/rakibul-hasan-cv.pdf" download
           class="inline-flex items-center gap-2 px-5 py-3 border border-gold text-gold font-mono text-xs tracking-widest uppercase rounded-full w-fit hover:bg-gold hover:text-ink transition-all duration-300">
          Download CV
        </a>
      </div>
    </div>
  </header>
</template>
