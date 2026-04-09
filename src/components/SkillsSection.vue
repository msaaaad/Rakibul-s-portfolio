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

const skillGroups = [
  {
    icon: '⬡', category: 'Design Process',
    skills: ['User Research', 'Wireframing', 'Prototyping', 'Iterative Design', 'Competitor Analysis', 'UX Audit', 'User-Centered Design', 'Information Architecture', 'User Flow Diagrams'],
  },
  {
    icon: '◈', category: 'Visual Design',
    skills: ['UI Design', 'Product Design', 'Visual Design', 'Color Theory', 'Typography', 'Design System', 'Landing Page Design', 'Mobile App Design'],
  },
  {
    icon: '◎', category: 'Tools',
    skills: ['Figma', 'FigJam', 'Microsoft Word', 'Microsoft Excel'],
  },
  {
    icon: '◉', category: 'Soft Skills',
    skills: ['Communication', 'Leadership', 'Analytical Skill', 'Time Management', 'Problem Solving', 'Team Work', 'Collaboration'],
  },
]

const marqueeSkills = ['Figma', 'UI Design', 'UX Research', 'Prototyping', 'Design Systems', 'Product Design', 'Wireframing', 'Color Theory', 'Typography', 'User Flows', 'Mobile Apps', 'FigJam']
const delayClass = (i: number) => `animate-delay-${(i + 1) * 100}`
</script>

<template>
  <section id="skills" ref="sectionRef" class="py-32 px-6 bg-white/[0.01]">
    <div class="max-w-6xl mx-auto">
      <div class="mb-16">
        <div class="hidden-init" :class="visible ? 'animate-fade-up' : ''">
          <span class="section-label">03 — Skills & Expertise</span>
        </div>
        <h2 class="font-display mt-5 text-paper hidden-init" :class="visible ? 'animate-fade-up animate-delay-200' : ''"
            style="font-size: clamp(2rem, 4vw, 3rem); font-weight: 700;">
          What I Bring to the Table
        </h2>
      </div>

      <!-- Skills grid -->
      <div class="grid grid-cols-1 md:grid-cols-2 gap-5">
        <div v-for="(group, i) in skillGroups" :key="group.category"
             class="p-7 rounded-2xl border border-white/5 bg-white/[0.02] hidden-init"
             :class="visible ? `animate-fade-up ${delayClass(i)}` : ''">
          <div class="flex items-center gap-3 mb-6">
            <span class="text-2xl text-gold">{{ group.icon }}</span>
            <h3 class="font-display text-lg font-semibold text-paper">{{ group.category }}</h3>
          </div>
          <div class="flex flex-wrap gap-2">
            <span v-for="skill in group.skills" :key="skill" class="tag-pill">{{ skill }}</span>
          </div>
        </div>
      </div>

      <!-- Certification -->
      <div class="mt-8 p-7 rounded-2xl border border-gold/20 bg-gradient-to-br from-gold/6 to-ink/90 hidden-init"
           :class="visible ? 'animate-fade-up animate-delay-500' : ''">
        <div class="flex flex-col sm:flex-row items-start sm:items-center justify-between gap-4">
          <div class="flex items-center gap-5">
            <div class="w-12 h-12 rounded-xl flex items-center justify-center text-xl bg-gold/10 border border-gold/30">🏆</div>
            <div>
              <p class="section-label mb-1">Certification</p>
              <h4 class="font-display text-xl font-semibold text-paper">UI UX Guided Program</h4>
              <p class="font-mono text-xs mt-1 text-dim">Ostad · 2023 · Credential ID: C6132</p>
            </div>
          </div>
          <a href="#" class="flex items-center gap-2 px-5 py-2.5 font-mono text-xs tracking-widest uppercase rounded-full border border-gold/30 text-gold hover:bg-gold/10 transition-all duration-300">
            View Certificate ↗
          </a>
        </div>
      </div>
    </div>

    <!-- Marquee -->
    <div class="mt-20 overflow-hidden hidden-init" :class="visible ? 'animate-fade-in animate-delay-600' : ''">
      <div class="flex animate-marquee gap-0" style="width: max-content;">
        <div v-for="n in 2" :key="n" class="flex items-center gap-6 pr-6">
          <template v-for="skill in marqueeSkills" :key="`${skill}-${n}`">
            <span class="font-mono text-xs tracking-widest uppercase whitespace-nowrap text-gold/30">{{ skill }}</span>
            <span class="text-gold/20" style="font-size: 8px;">◆</span>
          </template>
        </div>
      </div>
    </div>
  </section>
</template>
