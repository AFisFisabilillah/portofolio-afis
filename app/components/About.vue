<script setup lang="ts">


import SectionTittle from "~/components/SectionTittle.vue";

const stats = [
  { value: '1+', label: 'Years Exp.' },
  { value: '10+', label: 'Projects' },
  { value: '5', label: 'Core Stacks' },
]


</script>

<template>
  <section id="about" class="relative min-h-screen w-full bg-black overflow-hidden py-24 px-6 md:px-16">

    <div class="pixel-grid absolute inset-0 z-0 opacity-[0.03]" />

    <div class="relative z-10 max-w-6xl mx-auto">

      <SectionTittle>
        About Me
      </SectionTittle>

      <div class="grid grid-cols-1 lg:grid-cols-2 gap-16  items-start">

        <div class="flex flex-col gap-6">

          <div class=" relative w-full max-w-[360px]">
            <span class="absolute -top-2 -left-2 w-5 h-5 border-t-2 border-l-2 border-primary z-10" />
            <span class="absolute -top-2 -right-2 w-5 h-5 border-t-2 border-r-2 border-primary z-10" />
            <span class="absolute -bottom-2 -left-2 w-5 h-5 border-b-2 border-l-2 border-primary z-10" />
            <span class="absolute -bottom-2 -right-2 w-5 h-5 border-b-2 border-r-2 border-primary z-10" />

            <div class="absolute top-3 left-3 w-full h-full border border-primary/20 bg-primary/5" />

            <div class="relative w-full aspect-[3/4] bg-[#0d0d0d] border border-primary/30 overflow-hidden">
              <img
                  src="../assets/image/foto_abis.png"
                  alt="Profile photo"
                  class="w-full h-full object-cover grayscale contrast-110"
              />
              <div class="scanlines absolute inset-0 pointer-events-none" />
            </div>
          </div>

          <div class="flex items-center gap-2.5  max-w-[360px]">
            <span class="relative flex size-2">
              <span class="animate-ping absolute inline-flex h-full w-full bg-primary opacity-75" />
              <span class="relative inline-flex size-2 bg-primary" />
            </span>
            <span class="font-mono text-[10px] tracking-[0.15em] text-primary uppercase">Available for work</span>
          </div>
        </div>

        <div class="flex lg:col-span-1 flex-col gap-12">

          <div>
            <p class="font-mono text-[10px] tracking-[0.25em] text-primary uppercase mb-3">Fullstack Developer</p>
            <h2 class="font-['Bebas_Neue'] text-8xl leading-[0.9] text-white mb-6">
              Afis<br /><span class="text-outline-green">Fisabillah</span>
            </h2>
            <p class="font-mono text-sm leading-[1.9] text-white/50 max-w-[480px]">
              Seorang Fullstack Developer dengan Berfokus kepada user experience dan keaman sistem.
              Berpengalaman membangun aplikasi web modern menggunakan <span class="text-primary">Vue.js</span>,
              <span class="text-primary">React Js</span>,
              <span class="text-primary">React Native</span>,
              <span class="text-primary">Php</span>,
              <span class="text-primary">Laravel</span>, <span class="text-primary">Java</span>, dan
              <span class="text-primary">Spring Boot</span> — dari REST API hingga UI yang responsif dan scalable.
            </p>
          </div>

          <div class="grid grid-cols-3 gap-px border border-primary/15 bg-primary/15 max-w-[360px]">
            <div
                v-for="stat in stats"
                :key="stat.label"
                class="bg-black flex flex-col items-center py-5 gap-1"
            >
              <span class="font-['Bebas_Neue'] text-3xl text-primary leading-none">{{ stat.value }}</span>
              <span class="font-mono text-[9px] tracking-[0.2em] text-white/30 uppercase">{{ stat.label }}</span>
            </div>
          </div>

          <div class="flex items-center gap-4">
            <a
                href="#contact"
                class="inline-flex items-center gap-2 bg-primary text-black font-mono text-[10px] font-bold tracking-[0.2em] uppercase px-6 py-3 border-2 border-primary transition-all duration-200 hover:bg-transparent hover:text-primary"
            >
              HIRE ME
              <svg width="14" height="14" viewBox="0 0 16 16" fill="none">
                <path d="M3 8H13M13 8L8.5 3.5M13 8L8.5 12.5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
              </svg>
            </a>
            <a
                href="/cv.pdf"
                download
                class="inline-flex items-center gap-2 border border-primary/30 text-white/50 font-mono text-[10px] font-bold tracking-[0.2em] uppercase px-6 py-3 transition-all duration-200 hover:border-primary hover:text-primary"
            >
              DOWNLOAD CV
            </a>
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
  background-size: 40px 40px;
}

.scanlines {
  background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0, 0, 0, 0.15) 2px,
      rgba(0, 0, 0, 0.15) 4px
  );
}
</style>