<script setup lang="ts">
const year = new Date().getFullYear()
</script>

<template>
  <footer class="py-10 px-6 border-t border-gold/10">
    <div class="max-w-6xl mx-auto flex flex-col sm:flex-row items-center justify-between gap-4">
      <p class="font-mono text-xs tracking-widest uppercase text-dim">© {{ year }} Muhammad Rakibul Hasan diyen</p>
      <p class="font-mono text-xs text-dim/60">UI / UX Designer · Dhaka, Bangladesh</p>
      <div class="flex items-center gap-4">
        <a href="https://linkedin.com/in/muhammad-rakibul-hasan" target="_blank"
           class="font-mono text-xs tracking-widest uppercase text-dim hover:text-gold transition-colors duration-200">LinkedIn</a>
        <span class="text-gold/20">·</span>
        <a href="https://behance.net" target="_blank"
           class="font-mono text-xs tracking-widest uppercase text-dim hover:text-gold transition-colors duration-200">Behance</a>
        <span class="text-gold/20">·</span>
        <a href="/rakibul-hasan-cv.pdf" download
           class="font-mono text-xs tracking-widest uppercase text-gold hover:text-yellow-300 transition-colors duration-200">Download CV</a>
      </div>
    </div>
  </footer>
</template>
