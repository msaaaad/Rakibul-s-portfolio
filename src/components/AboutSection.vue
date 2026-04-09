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
  <section id="about" ref="sectionRef" class="py-32 px-6">
    <div class="max-w-6xl mx-auto grid grid-cols-1 lg:grid-cols-2 gap-20 items-center">

      <!-- Left: text -->
      <div>
        <div class="hidden-init" :class="visible ? 'animate-fade-up' : ''">
          <span class="section-label">01 — About</span>
        </div>

        <h2 class="font-display mt-5 leading-tight text-paper hidden-init" :class="visible ? 'animate-fade-up animate-delay-200' : ''"
            style="font-size: clamp(2.2rem, 5vw, 3.5rem); font-weight: 700;">
          Turning ideas into<br><em class="text-gold">intuitive</em> products
        </h2>

        <div class="mt-8 space-y-5 hidden-init" :class="visible ? 'animate-fade-up animate-delay-300' : ''">
          <p class="text-muted leading-relaxed">
            I'm a passionate UI/UX designer committed to full-time engagement in the creative realm
            of user experience and product design. My extensive experience spans collaborations with
            startups and digital agencies across multiple countries.
          </p>
          <p class="text-muted leading-relaxed">
            My journey is marked by dedication to delivering outstanding UX solutions — aligning closely
            with client objectives and conducting thorough assessments to ensure my work not only meets
            but exceeds expectations.
          </p>
        </div>

        <!-- Languages -->
        <div class="mt-10 hidden-init" :class="visible ? 'animate-fade-up animate-delay-400' : ''">
          <p class="section-label mb-4">Languages</p>
          <div class="flex flex-wrap gap-3">
            <div v-for="[lang, level] in [['Bangla','Native'],['English','Fluent'],['Hindi','Conversational'],['Arabic','Learner']]"
                 :key="lang"
                 class="flex items-center gap-2 px-4 py-2 rounded-full border border-gold/15 bg-gold/5">
              <span class="text-paper text-sm">{{ lang }}</span>
              <span class="text-gold font-mono text-xs">{{ level }}</span>
            </div>
          </div>
        </div>
      </div>

      <!-- Right: info card -->
      <div class="hidden-init" :class="visible ? 'animate-fade-up animate-delay-300' : ''">
        <div class="relative p-8 rounded-3xl border border-gold/15 bg-gradient-to-br from-gold/5 to-ink/80">
          <!-- Top accent -->

          <!-- Avatar + name -->
          <div class="flex items-center gap-5 mb-8">
            <div class="w-16 h-16 rounded-2xl flex items-center justify-center font-display text-2xl font-bold text-gold border border-gold/30 bg-gold/10 animate-pulse-glow">
              MR
            </div>
            <div>
              <p class="font-display text-xl font-semibold text-paper">Muhammad Rakibul Hasan</p>
              <p class="font-mono text-xs tracking-wider mt-1 text-gold">UI / UX Designer</p>
            </div>
          </div>

          <div class="space-y-4">
            <div v-for="[icon, label, value] in [
              ['📍','Location','Dhaka, Bangladesh'],
              ['✉️','Email','hello.rakibulh@gmail.com'],
              ['📞','Phone','+880 1688 251829'],
              ['🎓','Education','BSC in EEE — 2020'],
            ]" :key="label" class="flex items-start gap-4 pb-4 border-b border-gold/8">
              <span class="text-base mt-0.5">{{ icon }}</span>
              <div>
                <p class="font-mono text-xs tracking-wider mb-0.5 text-dim uppercase">{{ label }}</p>
                <p class="text-paper text-sm">{{ value }}</p>
              </div>
            </div>
          </div>

          <!-- Social links -->
          <div class="mt-6 flex gap-3">
            <a href="https://www.linkedin.com/in/mrakibux" target="_blank"
               class="flex-1 py-2.5 text-center font-mono text-xs tracking-wider uppercase rounded-full border border-gold/20 text-gold hover:bg-gold/10 transition-all duration-300">
              LinkedIn
            </a>
            <a href="https://www.behance.net/mrakibux" target="_blank"
               class="flex-1 py-2.5 text-center font-mono text-xs tracking-wider uppercase rounded-full border border-gold/20 text-gold hover:bg-gold/10 transition-all duration-300">
              Behance
            </a>
            <a href="/rakibul-hasan-cv.pdf" download
               class="flex-1 py-2.5 text-center font-mono text-xs tracking-wider uppercase rounded-full border border-gold/30 bg-gold/15 text-gold hover:bg-gold/25 transition-all duration-300">
              CV ↓
            </a>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
