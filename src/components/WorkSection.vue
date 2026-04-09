<script setup lang="ts">
import { ref, onMounted } from 'vue'

interface Experience {
  id: number; role: string; type: string; company: string
  period: string; location: string; description: string; tags: string[]
}

const experiences: Experience[] = [
  {
    id: 1, role: 'Junior UI UX Engineer', type: 'Full Time', company: 'Annonlab',
    period: 'Jan 2025 – Present', location: 'Remote · Dhaka',
    description: 'Working in a SaaS product-based company, focused on the full UI & UX lifecycle — from research and wireframing to polished high-fidelity designs.',
    tags: ['Product Design', 'UI Design', 'Research'],
  },
  {
    id: 2, role: 'Junior UI UX Designer', type: 'Full Time', company: 'We Are The Nexts',
    period: 'Nov 2024 – Dec 2024', location: 'Remote · UAE',
    description: 'Led UI/UX design for the "Click to Food" mobile application — covering flows, visual design, and competitive analysis for a product-based company.',
    tags: ['Product Design', 'UI Design', 'Research', 'Competitor Analysis'],
  },
  {
    id: 3, role: 'UI UX Designer', type: 'Full Time', company: 'Little Programmers',
    period: 'Oct 2023 – Aug 2024', location: 'Onsite · Sylhet',
    description: 'Startup environment — a whirlwind of creativity. Fostered rapid growth through iterative design, user research, and constant skill refinement to deliver impactful solutions.',
    tags: ['User Research', 'Competitor Analysis', 'Iterative Design', 'Prototyping', 'Wireframing', 'Leadership'],
  },
  {
    id: 4, role: 'UI UX Designer', type: 'Internship', company: 'Maximal Digitals',
    period: 'Jun 2023 – Aug 2023', location: 'Remote',
    description: 'Remote collaboration with global teams. Deep involvement in landing page design, mobile app design, UX audits, and design systems. Strong foundations in information architecture.',
    tags: ['Landing Page Design', 'Mobile App Design', 'UX Audit', 'Design System', 'Color Theory', 'Typography'],
  },
]

const sectionRef = ref<HTMLElement | null>(null)
const visible = ref(false)
const activeCard = ref<number | null>(null)

onMounted(() => {
  const observer = new IntersectionObserver(
    ([entry]) => { if (entry?.isIntersecting) { visible.value = true; observer.disconnect() } },
    { threshold: 0.1 }
  )
  if (sectionRef.value) observer.observe(sectionRef.value)
})

const delayClass = (i: number) => `animate-delay-${(i + 1) * 100}`
</script>

<template>
  <section id="work" ref="sectionRef" class="py-32 px-6">
    <div class="max-w-6xl mx-auto">
      <div class="mb-16">
        <div class="hidden-init" :class="visible ? 'animate-fade-up' : ''">
          <span class="section-label">02 — Work Experience</span>
        </div>
        <h2 class="font-display mt-5 text-paper hidden-init" :class="visible ? 'animate-fade-up animate-delay-200' : ''"
            style="font-size: clamp(2rem, 4vw, 3rem); font-weight: 700;">
          Where I've Created
        </h2>
      </div>

      <!-- Timeline -->
      <div class="relative">
        <div class="absolute hidden lg:block w-px top-0 bottom-0" style="left: 24px; background: linear-gradient(to bottom, transparent, #c8a96e40, transparent);" />

        <div class="space-y-5">
          <div v-for="(exp, index) in experiences" :key="exp.id"
               class="hidden-init" :class="visible ? `animate-fade-up ${delayClass(index)}` : ''">
            <div class="relative lg:pl-16 group" @mouseenter="activeCard = exp.id" @mouseleave="activeCard = null">
              <!-- Dot -->
              <div class="absolute hidden lg:flex items-center justify-center w-5 h-5 rounded-full border transition-all duration-300"
                   :class="activeCard === exp.id ? 'border-gold bg-gold/20' : 'border-gold/30'"
                   style="left: 16px; top: 24px;">
                <div class="w-2 h-2 rounded-full bg-gold transition-opacity duration-300"
                     :class="activeCard === exp.id ? 'opacity-100' : 'opacity-40'" />
              </div>

              <!-- Card -->
              <div class="p-7 rounded-2xl border transition-all duration-300 cursor-default"
                   :class="activeCard === exp.id
                     ? 'border-gold/30 bg-gradient-to-br from-gold/7 to-ink/90 translate-x-1'
                     : 'border-white/5 bg-white/[0.02]'">
                <div class="flex flex-col sm:flex-row sm:items-start justify-between gap-4 mb-5">
                  <div>
                    <div class="flex items-center flex-wrap gap-3 mb-1">
                      <h3 class="font-display text-xl font-semibold text-paper">{{ exp.role }}</h3>
                      <span class="tag-pill text-xs py-0">{{ exp.type }}</span>
                    </div>
                    <p class="font-mono text-sm text-gold">{{ exp.company }}</p>
                  </div>
                  <div class="text-left sm:text-right shrink-0">
                    <p class="font-mono text-xs text-dim">{{ exp.period }}</p>
                    <p class="font-mono text-xs text-dim mt-1">{{ exp.location }}</p>
                  </div>
                </div>
                <p class="text-sm leading-relaxed text-muted mb-5">{{ exp.description }}</p>
                <div class="flex flex-wrap gap-2">
                  <span v-for="tag in exp.tags" :key="tag" class="tag-pill">{{ tag }}</span>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
