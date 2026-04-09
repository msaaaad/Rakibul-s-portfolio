<script setup lang="ts">
import { ref, onMounted } from 'vue'

const sectionRef = ref<HTMLElement | null>(null)
const visible = ref(false)

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry?.isIntersecting) { visible.value = true; observer.disconnect() } },
    { threshold: 0.1 }
  )
  if (sectionRef.value) observer.observe(sectionRef.value)
})
</script>

<template>
  <section id="contact" ref="sectionRef" class="py-32 px-6">
    <div class="max-w-6xl mx-auto">

      <!-- Big CTA card -->
      <div class="relative overflow-hidden rounded-3xl p-12 md:p-20 border border-gold/20 bg-gradient-to-br from-gold/10 to-ink/95 hidden-init"
           :class="visible ? 'animate-fade-up' : ''">
        <!-- Decorative ring -->
        <div class="absolute top-0 right-0 w-96 h-96 opacity-10 pointer-events-none">
          <svg class="animate-spin-slow" viewBox="0 0 400 400" fill="none">
            <circle cx="200" cy="200" r="190" stroke="#c8a96e" stroke-width="1" stroke-dasharray="8 12"/>
            <circle cx="200" cy="200" r="130" stroke="#c8a96e" stroke-width="0.5" stroke-dasharray="4 8"/>
          </svg>
        </div>

        <div class="relative z-10 text-center max-w-2xl mx-auto">
          <span class="section-label block mb-5 hidden-init" :class="visible ? 'animate-fade-up animate-delay-200' : ''">
            04 — Let's Connect
          </span>
          <h2 class="font-display leading-tight text-paper hidden-init" :class="visible ? 'animate-fade-up animate-delay-300' : ''"
              style="font-size: clamp(2.5rem, 6vw, 4.5rem); font-weight: 700;">
            Got a Project<br>in Mind?
          </h2>
          <p class="mt-6 text-lg leading-relaxed text-muted hidden-init" :class="visible ? 'animate-fade-up animate-delay-400' : ''">
            I'm currently open to new opportunities. Whether you have a question, a project,
            or just want to say hello — my inbox is always open.
          </p>
          <div class="mt-10 flex flex-wrap gap-4 justify-center hidden-init" :class="visible ? 'animate-fade-up animate-delay-500' : ''">
            <a href="mailto:hello.rakibulh@gmail.com" class="btn-primary">Say Hello ✉</a>
            <a href="/rakibul-hasan-cv.pdf" download class="btn-outline">
              <svg width="14" height="14" viewBox="0 0 14 14" fill="none">
                <path d="M7 1v9M4 7l3 4 3-4M1 13h12" stroke="#c8a96e" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
              Download CV
            </a>
          </div>
        </div>
      </div>

      <!-- Contact links -->
      <div class="mt-6 grid grid-cols-1 sm:grid-cols-3 gap-4 hidden-init" :class="visible ? 'animate-fade-up animate-delay-600' : ''">
        <a v-for="[icon, label, value, href] in [
          ['✉', 'Email', 'hello.rakibulh@gmail.com', 'mailto:hello.rakibulh@gmail.com'],
          ['☎', 'Phone', '+880 1688 251829', 'tel:+8801688251829'],
          ['🔗', 'LinkedIn', 'Muhammad Rakibul Hasan', 'https://linkedin.com/in/muhammad-rakibul-hasan'],
        ]" :key="label" :href="href" target="_blank"
           class="flex items-center gap-4 p-5 rounded-2xl border border-white/5 bg-white/[0.02] hover:border-gold/30 hover:bg-gold/5 transition-all duration-300 group">
          <span class="text-xl">{{ icon }}</span>
          <div>
            <p class="font-mono text-xs tracking-wider uppercase mb-1 text-dim">{{ label }}</p>
            <p class="text-sm text-paper">{{ value }}</p>
          </div>
        </a>
      </div>
    </div>
  </section>
</template>
