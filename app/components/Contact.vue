<script setup lang="ts">
const contactMethods = [
  {
    id: '01',
    label: 'Email',
    value: 'afisfisabillah@gmail.com',
    href: 'mailto:afisfisabillah@gmail.com',
    meta: 'Primary channel',
  },
  {
    id: '02',
    label: 'Github',
    value: 'AFisFisabilillah',
    href: 'https://github.com/AFisFisabilillah',
    meta: 'Code repository',
  },
  {
    id: '03',
    label: 'Location',
    value: 'Bekasi, Indonesia',
    href: '#contact',
    meta: 'Remote ready',
  },
]

const responseSteps = [
  'Project brief',
  'Technical scope',
  'Build timeline',
  'Launch plan',
]
</script>

<template>
  <section id="contact" class="relative min-h-screen w-full bg-black overflow-hidden py-24 px-6 md:px-16">
    <div class="pixel-grid absolute inset-0 z-0 opacity-[0.035]" />
    <div class="absolute top-0 left-0 w-px h-full bg-primary/10 z-0" />
    <div class="absolute top-0 right-0 w-px h-full bg-primary/10 z-0" />

    <div class="relative z-10 max-w-6xl mx-auto">
      <SectionTittle>
        Contact
      </SectionTittle>

      <div class="flex flex-col md:flex-row md:items-end md:justify-between gap-6 mb-14">
        <h2 class="font-['Bebas_Neue'] text-[clamp(52px,9vw,104px)] leading-[0.88] text-white">
          LET'S<br /><span class="text-outline-green">CONNECT</span>
        </h2>
        <p class="font-mono text-sm leading-[1.9] text-white/35 max-w-sm md:text-right">
          Siap membantu membangun aplikasi web, mobile, dan backend yang rapi dari ide sampai produksi.
        </p>
      </div>

      <div class="grid grid-cols-1 lg:grid-cols-[1.05fr_0.95fr] gap-px bg-primary/10 border border-primary/10">
        <div class="relative bg-black p-6 md:p-10 overflow-hidden">
          <span class="absolute top-4 left-4 w-5 h-5 border-t border-l border-primary/50" />
          <span class="absolute top-4 right-4 w-5 h-5 border-t border-r border-primary/50" />
          <span class="absolute bottom-4 left-4 w-5 h-5 border-b border-l border-primary/50" />
          <span class="absolute bottom-4 right-4 w-5 h-5 border-b border-r border-primary/50" />

          <div class="relative z-10 flex flex-col min-h-[420px]">
            <div class="flex items-center gap-2.5 mb-8">
              <span class="relative flex size-2">
                <span class="animate-ping absolute inline-flex h-full w-full bg-primary opacity-75" />
                <span class="relative inline-flex size-2 bg-primary" />
              </span>
              <span class="font-mono text-[10px] tracking-[0.2em] text-primary uppercase">Available for freelance</span>
            </div>

            <p class="font-mono text-[10px] tracking-[0.28em] text-primary/60 uppercase mb-3">
              // Start a project
            </p>
            <h3 class="font-['Bebas_Neue'] text-[clamp(38px,6vw,72px)] leading-[0.95] text-white mb-6">
              BUILD SOMETHING<br />
              <span class="text-outline-green">SOLID</span>
            </h3>
            <p class="font-mono text-sm leading-[1.9] text-white/45 max-w-lg">
              Ceritakan kebutuhan produk, fitur utama, dan target rilis. Saya akan bantu susun solusi teknis yang realistis dan mudah dikembangkan.
            </p>

            <div class="grid grid-cols-2 sm:grid-cols-4 gap-px bg-primary/15 mt-10">
              <div
                  v-for="(step, index) in responseSteps"
                  :key="step"
                  class="bg-black px-4 py-5"
              >
                <p class="font-mono text-[9px] tracking-[0.2em] text-primary/45 mb-2">
                  {{ String(index + 1).padStart(2, '0') }}
                </p>
                <p class="font-mono text-[10px] font-bold tracking-[0.12em] text-white/55 uppercase leading-relaxed">
                  {{ step }}
                </p>
              </div>
            </div>

            <div class="mt-auto pt-10">
              <a
                  href="mailto:afisfisabillah@gmail.com?subject=Project%20Inquiry"
                  class="inline-flex items-center gap-2 bg-primary text-black font-mono text-[10px] font-bold tracking-[0.2em] uppercase px-6 py-3 border-2 border-primary transition-all duration-200 hover:bg-transparent hover:text-primary"
              >
                SEND MESSAGE
                <svg width="14" height="14" viewBox="0 0 16 16" fill="none">
                  <path d="M3 8H13M13 8L8.5 3.5M13 8L8.5 12.5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
              </a>
            </div>
          </div>

          <div class="scanlines absolute inset-0 pointer-events-none opacity-20" />
        </div>

        <div class="bg-black flex flex-col">
          <a
              v-for="method in contactMethods"
              :key="method.id"
              :href="method.href"
              class="group relative flex items-center justify-between gap-5 px-6 py-7 md:px-8 md:py-8 border-b border-primary/10 transition-all duration-200 hover:bg-primary/[0.04]"
          >
            <div class="absolute left-0 top-0 h-full w-0.5 bg-transparent transition-all duration-300 group-hover:bg-primary" />
            <div>
              <div class="flex items-center gap-3 mb-3">
                <span class="font-mono text-[9px] font-bold tracking-[0.2em] text-white/20 group-hover:text-primary/50 transition-colors">
                  {{ method.id }}
                </span>
                <span class="w-px h-3 bg-white/10" />
                <span class="font-mono text-[9px] tracking-[0.2em] text-primary/60 uppercase">
                  {{ method.meta }}
                </span>
              </div>
              <p class="font-['Bebas_Neue'] text-3xl tracking-wide text-white group-hover:text-primary transition-colors duration-200">
                {{ method.label }}
              </p>
              <p class="font-mono text-xs text-white/35 mt-1 break-all">
                {{ method.value }}
              </p>
            </div>
            <span class="grid size-10 place-items-center border border-primary/20 text-primary transition-all duration-200 group-hover:bg-primary group-hover:text-black">
              <svg width="14" height="14" viewBox="0 0 16 16" fill="none">
                <path d="M5 3H13M13 3V11M13 3L3 13" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
            </span>
          </a>

          <div class="mt-auto p-6 md:p-8">
            <p class="font-mono text-[9px] tracking-[0.25em] text-white/20 uppercase mb-4">// Signal</p>
            <div class="flex gap-px">
              <span
                  v-for="i in 32"
                  :key="i"
                  class="h-2 flex-1"
                  :class="i % 4 === 0 ? 'bg-primary' : 'bg-primary/15'"
              />
            </div>
            <p class="font-mono text-[10px] tracking-[0.16em] text-white/25 uppercase mt-4">
              Response target: 24 hours
            </p>
          </div>
        </div>
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

.pixel-grid {
  background-image:
      linear-gradient(rgba(167,239,158,1) 1px, transparent 1px),
      linear-gradient(90deg, rgba(167,239,158,1) 1px, transparent 1px);
  background-size: 36px 36px;
}

.scanlines {
  background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.22) 2px,
      rgba(0,0,0,0.22) 4px
  );
}
</style>
