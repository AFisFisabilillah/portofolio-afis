<script setup lang="ts">
const experiences = [
  {
    id: '01',
    year: 'Juni 2025 - Present',
    role: 'Freelance Fullstack  Developer',
    company: 'PT Satria Media Teknologi',
    type: 'Freelance',
    location: 'Remote',
    desc: 'Memimpin pengembangan aplikasi enterprise menggunakan Spring Boot dan Vue.js. Merancang arsitektur microservices, optimasi performa backend, dan membangun UI yang scalable.',
    stacks: ['Vue.js', 'Spring Boot', 'Java', 'PostgreSQL', 'Docker'],
    highlight: true,
  },
  {
    id: '02',
    year: 'Januari 2025 - Juni 2025',
    role: 'PKL Junior Programmer',
    company: 'PT Satria Media Teknologi',
    type: 'Full-time',
    location: 'Jatiasih, Bekasi, ID',
    desc: 'Membangun REST API dengan Laravel dan antarmuka pengguna interaktif menggunakan Vue.js. Bertanggung jawab atas integrasi third-party API dan manajemen database.',
    stacks: ['Vue.js', 'Laravel', 'MySQL', 'Redis'],
    highlight: false,
  },
]

const activeId = ref('01')
const activeExp = computed(() => experiences.find(e => e.id === activeId.value)!)
</script>

<template>
  <section id="experience" class="relative min-h-screen w-full bg-black overflow-hidden py-24 px-6 md:px-16">

    <div class="absolute top-0 left-0 w-px h-full bg-primary/10 z-0" />
    <div class="absolute top-0 right-0 w-px h-full bg-primary/10 z-0" />

    <div class="relative z-10 max-w-6xl mx-auto">

      <!-- Section label -->
     <SectionTittle>
       Experience
     </SectionTittle>

      <h2 class="font-['Bebas_Neue'] text-8xl leading-[0.9] text-white mb-16">
        My<br /><span class="text-outline-green">Experience</span>
      </h2>

      <div class="grid grid-cols-1 lg:grid-cols-2 gap-0 border border-primary/15">

        <div class="border-r border-primary/15">
          <button
              v-for="exp in experiences"
              :key="exp.id"
              class="w-full text-left px-6 py-6 border-b border-primary/10 transition-all duration-200 group relative"
              :class="activeId === exp.id ? 'bg-primary/5' : 'hover:bg-white/[0.02]'"
              @click="activeId = exp.id"
          >
            <div
                class="absolute left-0 top-0 h-full w-0.5 transition-all duration-300"
                :class="activeId === exp.id ? 'bg-primary' : 'bg-transparent'"
            />

            <div class="flex items-start justify-between gap-4">
              <div>
                <p class="font-mono text-[9px] tracking-[0.2em] text-primary/50 uppercase mb-1">
                  {{ exp.year }}
                </p>
                <p
                    class="font-['Bebas_Neue'] text-xl tracking-wide transition-colors duration-200"
                    :class="activeId === exp.id ? 'text-primary' : 'text-white/70 group-hover:text-white'"
                >
                  {{ exp.role }}
                </p>
                <p class="font-mono text-[10px] text-white/30 mt-0.5">{{ exp.company }}</p>
              </div>
              <span
                  class="font-mono text-[9px] font-bold tracking-[0.15em] uppercase px-2 py-1 border flex-shrink-0 transition-all duration-200"
                  :class="activeId === exp.id
                  ? 'border-primary/40 text-primary'
                  : 'border-white/10 text-white/20 group-hover:border-white/20 group-hover:text-white/40'"
              >
                {{ exp.id }}
              </span>
            </div>
          </button>

          <div class="px-6 py-5 flex items-center justify-between">
            <span class="font-mono text-[9px] tracking-[0.2em] text-white/20 uppercase">Total</span>
            <span class="font-mono text-[9px] tracking-[0.2em] text-white/20 uppercase">{{ experiences.length }} Positions</span>
          </div>
        </div>

        <Transition name="slide-fade" mode="out-in">
          <div :key="activeExp.id" class="p-8 md:p-10 flex flex-col gap-8">

            <div>
              <div class="flex items-center gap-2 mb-4">
                <span class="font-mono text-[9px] tracking-[0.2em] text-primary uppercase border border-primary/30 px-2 py-1">
                  {{ activeExp.type }}
                </span>
                <span class="font-mono text-[9px] tracking-[0.2em] text-white/30 uppercase">
                  {{ activeExp.location }}
                </span>
              </div>
              <h3 class="font-['Bebas_Neue'] text-[clamp(32px,5vw,56px)] leading-[0.95] text-white mb-1">
                {{ activeExp.role }}
              </h3>
              <p class="font-mono text-sm text-primary/70">@ {{ activeExp.company }}</p>
            </div>

            <div class="flex items-center gap-3">
              <div class="w-2 h-2 bg-primary" />
              <div class="flex-1 h-px bg-primary/15" />
            </div>

            <div class="flex items-center gap-6">
              <div>
                <p class="font-mono text-[9px] tracking-[0.2em] text-white/25 uppercase mb-1">Period</p>
                <p class="font-mono text-xs font-bold text-white/70">{{ activeExp.year }}</p>
              </div>
            </div>

            <p class="font-mono text-sm leading-[1.9] text-white/50">
              {{ activeExp.desc }}
            </p>

            <div>
              <p class="font-mono text-[9px] tracking-[0.25em] text-white/25 uppercase mb-3">// Tech Stack</p>
              <div class="flex flex-wrap gap-2">
                <span
                    v-for="stack in activeExp.stacks"
                    :key="stack"
                    class="font-mono text-[10px] font-bold tracking-[0.15em] uppercase px-3 py-1.5 border border-primary/20 text-primary/70 hover:border-primary/50 hover:text-primary transition-all duration-200"
                >
                  {{ stack }}
                </span>
              </div>
            </div>

            <!-- Navigation -->
            <div class="flex items-center justify-between pt-4 border-t border-primary/10 mt-auto">
              <button
                  class="font-mono text-[10px] tracking-[0.15em] uppercase text-white/25 hover:text-primary transition-colors flex items-center gap-2 disabled:opacity-20 disabled:cursor-not-allowed"
                  :disabled="activeId === experiences[0]?.id"
                  @click="activeId = experiences[experiences.findIndex(e => e.id === activeId) - 1]?.id ?? activeId"
              >
                <svg width="14" height="14" viewBox="0 0 16 16" fill="none">
                  <path d="M13 8H3M3 8L7.5 3.5M3 8L7.5 12.5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
                Prev
              </button>
              <span class="font-mono text-[9px] tracking-[0.2em] text-white/20">
                {{ experiences.findIndex(e => e.id === activeId) + 1 }} / {{ experiences.length }}
              </span>
              <button
                  class="font-mono text-[10px] tracking-[0.15em] uppercase text-white/25 hover:text-primary transition-colors flex items-center gap-2 disabled:opacity-20 disabled:cursor-not-allowed"
                  :disabled="activeId === experiences[experiences.length - 1]?.id"
                  @click="activeId = experiences[experiences.findIndex(e => e.id === activeId) + 1]?.id ?? activeId"
              >
                Next
                <svg width="14" height="14" viewBox="0 0 16 16" fill="none">
                  <path d="M3 8H13M13 8L8.5 3.5M13 8L8.5 12.5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
              </button>
            </div>

          </div>
        </Transition>
      </div>

    </div>
  </section>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap');

.text-outline-green {
  -webkit-text-stroke: 2px #A7EF9E;
  color: transparent;
}

.slide-fade-enter-active {
  transition: all 0.25s cubic-bezier(0.16, 1, 0.3, 1);
}
.slide-fade-leave-active {
  transition: all 0.15s ease-in;
}
.slide-fade-enter-from {
  opacity: 0;
  transform: translateY(12px);
}
.slide-fade-leave-to {
  opacity: 0;
  transform: translateY(-8px);
}
</style>