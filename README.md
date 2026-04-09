# Rakibul Hasan — Portfolio

A beautiful, production-grade portfolio website for Kazi Md. Rakibul Hasan, UI/UX Designer.

## Tech Stack
- **Vue 3** with Composition API & `<script setup>`
- **TypeScript** — strict type checking
- **Tailwind CSS v4** — via `@tailwindcss/vite`
- **Vite** — fast build tooling

## Getting Started

```bash
npm install
npm run dev        # development server
npm run build      # production build → ./dist
npm run preview    # preview production build
```

## Structure
```
src/
  components/
    NavBar.vue         # Sticky navigation with smooth scroll & CV download
    HeroSection.vue    # Hero with animated headline and stats
    AboutSection.vue   # Bio, languages, contact card
    WorkSection.vue    # Work experience timeline
    SkillsSection.vue  # Skills grid + certification + marquee
    ContactSection.vue # CTA + contact links
    FooterBar.vue      # Footer
  assets/
    main.css           # Global styles, fonts, animations
  App.vue
  main.ts

public/
  rakibul-hasan-cv.pdf  # CV file (downloadable)
```

## CV Download
The CV PDF is served from `public/rakibul-hasan-cv.pdf`. Replace it with the latest version as needed.

## Design
- Dark theme with warm gold (`#c8a96e`) accent
- Playfair Display (serif) + DM Sans + DM Mono
- Subtle grid background, rotating SVG rings, animated marquee
- Scroll-triggered entrance animations via IntersectionObserver
