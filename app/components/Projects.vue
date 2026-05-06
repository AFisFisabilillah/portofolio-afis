<script setup lang="ts">
const projects = [
  {
    id: '01',
    title: 'Primago',
    category: 'Application',
    year: '2025',
    desc: 'Aplikasi untuk penyaluran tenaga kerja keluar negri melalui Yayasa Abinggo Prima group',
    stacks: ['React Native', 'Laravel', 'Mysql', 'React Js'],
    image: '/images/primago.jpeg',
    link: 'https://apps.apple.com/id/app/primago/id6756656813?l=id',
    repo: '#',
    status: 'Live',
  },
  {
    id: '02',
    title: 'Stride Go',
    category: 'Application',
    year: '2025',
    desc: 'Applikasi untuk tracking olahraga mulai dari workout ringan serta lari dan juga terdapat fitur untuk latihan yang terstruktur',
    stacks: ['Supabase', 'React Native', 'Expo'],
    image: '/images/project_1.png',
    link: '#',
    repo: 'https://github.com/AFisFisabilillah/stridego',
    status: 'Live',
  },
  {
    id: '03',
    title: 'ERP Toko Komputer',
    category: 'Web Application',
    year: '2026',
    desc: 'Webiste unutk mengelola service unutk toko komputer, dilengkapi fitur tracking service barang sehingga user bisa melihat progress dari service nya',
    stacks: ['React js', 'Vite', 'MySQL', 'Laravel'],
    image: '/images/ahtaufix.png',
    link: 'www.ahtaufix.my.id',
    repo: '#',
    status: 'Live',
  },
  {
    id: '04',
    title: 'Gogatherly',
    category: 'Web Application, ',
    year: '2025-2026',
    desc: 'Web Applikasi untuk mengelola, mempromosikan serta menjual ticket dari sebuah event. Dilengkapi dengan payment gateway.',
    stacks: ['Vue.js', 'Java', 'Spring Boot', 'Postgresql', "Spring Security", "Kafka", "Midtrans", "Redis", "Docker"],
    image: '/images/gogatherly.png',
    link: '#',
    repo: '#',
    status: 'Archived',
  },
  {
    id: '05',
    title: 'Satria Pos',
    category: 'Web Application',
    year: '2025-2026',
    desc: 'Web Applikasi untuk pengelolan stok barang mulai dari metode FIFO dan LIFO. SERTA TERDAPAT MANAGEMENT KASIR UNTUK PEMBELIAN SEBUAH BARANG ',
    stacks: ["Laravel","React Js", "Inertia Js", "Mysql"],
    image: '/images/satriaPos.png',
    link: '#',
    repo: '#',
    status: 'Archived',
  },
]

const hoveredId = ref<string | null>(null)


</script>

<template>
  <section id="projects" class="relative min-h-screen w-full bg-black overflow-hidden py-24 px-6 md:px-16">

    <div class="absolute top-0 left-0 w-px h-full bg-primary/10 z-0" />
    <div class="absolute top-0 right-0 w-px h-full bg-primary/10 z-0" />

    <div class="relative z-10 max-w-6xl mx-auto">

     <SectionTittle>
       Projects
     </SectionTittle>

      <!-- Title -->
      <div class="flex flex-col md:flex-row md:items-end md:justify-between gap-6 mb-12">
        <h2 class="font-['Bebas_Neue'] text-[clamp(48px,8vw,96px)] leading-[0.9] text-white">
          SELECTED<br /><span class="text-outline-green">WORKS</span>
        </h2>
        <p class="font-mono text-sm text-white/30 max-w-xs leading-relaxed md:text-right">
          {{ projects.length }} projects shipped.<br />Each one built with purpose.
        </p>
      </div>

      

      <TransitionGroup name="grid-fade" tag="div" class="grid grid-cols-1 md:grid-cols-2 gap-px bg-primary/10">
        <div
            v-for="project in projects"
            :key="project.id"
            class="group relative bg-black flex flex-col overflow-hidden transition-all duration-300 hover:bg-primary/[0.02]"
            @mouseenter="hoveredId = project.id"
            @mouseleave="hoveredId = null"
        >
          <span class="absolute top-3 right-3 w-4 h-4 border-t border-r border-primary/0 group-hover:border-primary/50 transition-all duration-300 z-10" />
          <span class="absolute bottom-3 left-3 w-4 h-4 border-b border-l border-primary/0 group-hover:border-primary/50 transition-all duration-300 z-10" />

          <div class="relative w-full aspect-video bg-[#0a0a0a] border-b border-primary/10 overflow-hidden">
            <img
                :src="project.image"
                :alt="project.title"
                class="w-full h-full object-cover grayscale group-hover:grayscale-0 transition-all duration-500 scale-100 group-hover:scale-105"
                onerror="this.style.display='none'"
            />


            <div class="scanlines absolute inset-0 pointer-events-none opacity-30" />

            <div class="absolute top-3 left-3 flex items-center gap-1.5 bg-black/70 backdrop-blur-sm border border-primary/20 px-2.5 py-1">
              <span
                  class="w-1.5 h-1.5 rounded-full"
                  :class="project.status === 'Live' ? 'bg-primary animate-pulse' : 'bg-white/20'"
              />
              <span class="font-mono text-[9px] font-bold tracking-[0.15em] uppercase"
                    :class="project.status === 'Live' ? 'text-primary' : 'text-white/30'"
              >
                {{ project.status }}
              </span>
            </div>

            <div class="absolute top-3 right-3 bg-black/70 backdrop-blur-sm border border-white/10 px-2 py-1">
              <span class="font-mono text-[9px] text-white/40 tracking-[0.15em]">{{ project.year }}</span>
            </div>

            <div class="absolute inset-0 bg-black/60 flex items-center justify-center gap-4 opacity-0 group-hover:opacity-100 transition-opacity duration-300">
              <a
                  :href="project.link"
                  class="flex items-center gap-2 bg-primary text-black font-mono text-[10px] font-bold tracking-[0.15em] uppercase px-4 py-2 hover:bg-white transition-colors duration-200"
                  @click.stop
              >
                Live
                <svg width="10" height="10" viewBox="0 0 16 16" fill="none">
                  <path d="M3 8H13M13 8L8.5 3.5M13 8L8.5 12.5" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
                </svg>
              </a>
              <a
                  :href="project.repo"
                  class="flex items-center gap-2 border border-primary/50 text-primary font-mono text-[10px] font-bold tracking-[0.15em] uppercase px-4 py-2 hover:bg-primary/10 transition-colors duration-200"
                  @click.stop
              >
                <svg width="12" height="12" viewBox="0 0 24 24" fill="currentColor">
                  <path d="M12 0C5.37 0 0 5.37 0 12c0 5.31 3.435 9.795 8.205 11.385.6.105.825-.255.825-.57 0-.285-.015-1.23-.015-2.235-3.015.555-3.795-.735-4.035-1.41-.135-.345-.72-1.41-1.23-1.695-.42-.225-1.02-.78-.015-.795.945-.015 1.62.87 1.845 1.23 1.08 1.815 2.805 1.305 3.495.99.105-.78.42-1.305.765-1.605-2.67-.3-5.46-1.335-5.46-5.925 0-1.305.465-2.385 1.23-3.225-.12-.3-.54-1.53.12-3.18 0 0 1.005-.315 3.3 1.23.96-.27 1.98-.405 3-.405s2.04.135 3 .405c2.295-1.56 3.3-1.23 3.3-1.23.66 1.65.24 2.88.12 3.18.765.84 1.23 1.905 1.23 3.225 0 4.605-2.805 5.625-5.475 5.925.435.375.81 1.095.81 2.22 0 1.605-.015 2.895-.015 3.3 0 .315.225.69.825.57A12.02 12.02 0 0024 12c0-6.63-5.37-12-12-12z"/>
                </svg>
                Repo
              </a>
            </div>
          </div>

          <div class="p-6 flex flex-col gap-4 flex-1">

            <div class="flex items-center gap-2.5">
              <span class="font-mono text-[9px] font-bold text-white/15 tracking-[0.2em]">{{ project.id }}</span>
              <span class="w-px h-3 bg-white/10" />
              <span class="font-mono text-[9px] tracking-[0.2em] text-primary/60 uppercase border border-primary/20 px-2 py-0.5">
                {{ project.category }}
              </span>
            </div>

            <!-- Title -->
            <h3 class="font-['Bebas_Neue'] text-[clamp(24px,3.5vw,36px)] leading-none text-white group-hover:text-primary transition-colors duration-300">
              {{ project.title }}
            </h3>

            <!-- Desc -->
            <p class="font-mono text-[11px] leading-[1.8] text-white/35 flex-1">
              {{ project.desc }}
            </p>

            <!-- Stack -->
            <div class="flex flex-wrap gap-1.5 pt-2 border-t border-white/5 group-hover:border-primary/10 transition-colors duration-300">
              <span
                  v-for="stack in project.stacks"
                  :key="stack"
                  class="font-mono text-[9px] tracking-[0.12em] uppercase text-white/25 border border-white/8 px-2 py-1 group-hover:border-primary/20 group-hover:text-primary/50 transition-all duration-300"
              >
                {{ stack }}
              </span>
            </div>

          </div>
        </div>
      </TransitionGroup>
    </div>
  </section>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap');

.text-outline-green {
  -webkit-text-stroke: 2px #A7EF9E;
  color: transparent;
}

img + .img-fallback { display: none; }
img[style*="display: none"] + .img-fallback { display: flex; }

.grid-pattern {
  background-image:
      linear-gradient(rgba(167,239,158,1) 1px, transparent 1px),
      linear-gradient(90deg, rgba(167,239,158,1) 1px, transparent 1px);
  background-size: 20px 20px;
}

.scanlines {
  background: repeating-linear-gradient(
      0deg,
      transparent,
      transparent 2px,
      rgba(0,0,0,0.2) 2px,
      rgba(0,0,0,0.2) 4px
  );
}

.grid-fade-enter-active,
.grid-fade-leave-active {
  transition: all 0.25s ease;
}
.grid-fade-enter-from,
.grid-fade-leave-to {
  opacity: 0;
  transform: translateY(10px);
}
.grid-fade-move {
  transition: transform 0.3s ease;
}
</style>