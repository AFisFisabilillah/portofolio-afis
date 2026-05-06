<script setup lang="ts">
const categories = [
  {
    id: 'frontend',
    label: 'Frontend',
    code: '01',
    skills: [
      { name: 'Vue.js',    level: 95 },
      { name: 'Nuxt.js',  level: 88 },
      { name: 'React.js', level: 80 },
      { name: 'Vite',     level: 85 },
    ],
  },
  {
    id: 'backend',
    label: 'Backend',
    code: '02',
    skills: [
      { name: 'Laravel',     level: 90 },
      { name: 'PHP',         level: 88 },
      { name: 'Spring Boot', level: 82 },
      { name: 'Java',        level: 80 },
    ],
  },
  {
    id: 'database',
    label: 'Database',
    code: '03',
    skills: [
      { name: 'MySQL',      level: 90 },
      { name: 'PostgreSQL', level: 85 },
      { name: 'Redis',      level: 75 },
    ],
  },
  {
    id: 'tools',
    label: 'Tools',
    code: '04',
    skills: [
      { name: 'Docker', level: 80 },
      { name: 'Kafka',  level: 70 },
    ],
  },
]

const activeCategory = ref('frontend')
const active = computed(() => categories.find(c => c.id === activeCategory.value)!)
const totalSkills = categories.reduce((acc, c) => acc + c.skills.length, 0)

const allSkills = computed(() =>
    categories.flatMap(cat =>
        cat.skills.map(skill => ({ ...skill, catId: cat.id }))
    )
)

const levelLabel = (level: number) => {
  if (level >= 90) return 'Expert'
  if (level >= 80) return 'Advanced'
  if (level >= 70) return 'Proficient'
  return 'Familiar'
}
</script>

<template>
  <section id="skills" class="relative w-full bg-black overflow-hidden py-24 px-6 md:px-16">

    <div class="absolute top-0 left-0 w-px h-full bg-[#A7EF9E]/10 z-0" />
    <div class="absolute top-0 right-0 w-px h-full bg-[#A7EF9E]/10 z-0" />

    <div class="relative z-10 max-w-6xl mx-auto">

      <!-- Section label -->
      <div class="flex items-center gap-3 mb-4">
        <span class="w-6 h-px bg-[#A7EF9E]" />
        <span class="font-mono text-[10px] font-bold tracking-[0.3em] text-[#A7EF9E] uppercase">Skills</span>
        <span class="w-6 h-px bg-[#A7EF9E]" />
      </div>

      <!-- Title -->
      <div class="flex flex-col md:flex-row md:items-end md:justify-between gap-4 mb-16">
        <h2 class="font-['Bebas_Neue'] text-[clamp(48px,8vw,96px)] leading-[0.9] text-white">
          TECH<br /><span class="text-outline-green">STACK</span>
        </h2>
        <p class="font-mono text-sm text-white/30 md:text-right leading-relaxed">
          {{ totalSkills }} technologies.<br />4 domains of expertise.
        </p>
      </div>

      <!-- Main layout -->
      <div class="grid grid-cols-1 lg:grid-cols-[260px_1fr] gap-px bg-[#A7EF9E]/10">

        <!-- LEFT: Category tabs -->
        <div class="bg-black flex flex-col">
          <button
              v-for="cat in categories"
              :key="cat.id"
              class="relative w-full text-left px-6 py-6 border-b border-[#A7EF9E]/10 group transition-all duration-200"
              :class="activeCategory === cat.id ? 'bg-[#A7EF9E]/5' : 'hover:bg-white/[0.02]'"
              @click="activeCategory = cat.id"
          >
            <div
                class="absolute left-0 top-0 h-full w-0.5 transition-all duration-300"
                :class="activeCategory === cat.id ? 'bg-[#A7EF9E]' : 'bg-transparent'"
            />
            <div class="flex items-center justify-between mb-3">
              <div>
                <p class="font-mono text-[9px] tracking-[0.25em] text-white/20 uppercase mb-1">{{ cat.code }}</p>
                <p
                    class="font-['Bebas_Neue'] text-2xl tracking-wide transition-colors duration-200"
                    :class="activeCategory === cat.id ? 'text-[#A7EF9E]' : 'text-white/50 group-hover:text-white'"
                >
                  {{ cat.label }}
                </p>
              </div>
              <span class="font-mono text-[10px] text-white/20">{{ cat.skills.length }}x</span>
            </div>
            <!-- Mini pixel bar -->
            <div class="flex gap-px">
              <div
                  v-for="i in 10"
                  :key="i"
                  class="h-0.5 flex-1 transition-all duration-300"
                  :class="activeCategory === cat.id
                  ? (i <= 7 ? 'bg-[#A7EF9E]' : 'bg-[#A7EF9E]/20')
                  : 'bg-white/8'"
              />
            </div>
          </button>

          <!-- Total -->
          <div class="px-6 py-5 mt-auto border-t border-[#A7EF9E]/10">
            <p class="font-mono text-[9px] tracking-[0.2em] text-white/20 uppercase">Total Skills</p>
            <p class="font-['Bebas_Neue'] text-3xl text-[#A7EF9E] mt-1">{{ totalSkills }}</p>
          </div>
        </div>

        <!-- RIGHT: Skill detail -->
        <Transition name="slide-fade" mode="out-in">
          <div :key="active.id" class="bg-black p-8 md:p-10 flex flex-col gap-10">

            <!-- Header -->
            <div class="flex items-start justify-between">
              <div>
                <p class="font-mono text-[9px] tracking-[0.3em] text-[#A7EF9E]/50 uppercase mb-2">
                  {{ active.code }} / {{ active.label }}
                </p>
                <h3 class="font-['Bebas_Neue'] text-[clamp(36px,5vw,64px)] leading-none text-white">
                  {{ active.label.toUpperCase() }}<br />
                  <span class="text-outline-green">SKILLS</span>
                </h3>
              </div>
              <!-- Decorative pixel cluster -->
              <div class="hidden md:grid grid-cols-4 gap-px opacity-25 flex-shrink-0">
                <div
                    v-for="i in 16"
                    :key="i"
                    class="w-2 h-2"
                    :class="i % 3 === 0 ? 'bg-[#A7EF9E]' : 'bg-[#A7EF9E]/20'"
                />
              </div>
            </div>

            <!-- Skills list -->
            <div class="flex flex-col gap-7">
              <div
                  v-for="skill in active.skills"
                  :key="skill.name"
                  class="group/skill flex flex-col gap-2"
              >
                <div class="flex items-center justify-between">
                  <div class="flex items-center gap-3">
                    <div class="w-1.5 h-1.5 bg-[#A7EF9E] flex-shrink-0" />
                    <span class="font-['Bebas_Neue'] text-2xl tracking-wide text-white group-hover/skill:text-[#A7EF9E] transition-colors duration-200">
                      {{ skill.name }}
                    </span>
                  </div>
                  <div class="flex items-center gap-3">
                    <span class="font-mono text-[9px] tracking-[0.15em] text-white/25 uppercase">
                      {{ levelLabel(skill.level) }}
                    </span>
                    <span class="font-mono text-xs font-bold text-[#A7EF9E]">
                      {{ skill.level }}<span class="text-white/20">%</span>
                    </span>
                  </div>
                </div>

                <!-- Pixel progress bar — 25 blocks -->
                <div class="flex gap-px">
                  <div
                      v-for="i in 25"
                      :key="i"
                      class="h-2 flex-1 transition-all duration-200"
                      :class="i <= Math.round(skill.level / 4)
                      ? 'bg-[#A7EF9E] group-hover/skill:bg-[#A7EF9E]'
                      : 'bg-[#A7EF9E]/10'"
                  />
                </div>
              </div>
            </div>

            <!-- All skills chip cloud -->
            <div class="border-t border-[#A7EF9E]/10 pt-8">
              <p class="font-mono text-[9px] tracking-[0.25em] text-white/20 uppercase mb-4">// All Technologies</p>
              <div class="flex flex-wrap gap-2">
                <span
                    v-for="skill in allSkills"
                    :key="`${skill.catId}-${skill.name}`"
                    class="font-mono text-[10px] font-bold tracking-[0.12em] uppercase px-3 py-1.5 border transition-all duration-200 cursor-default"
                    :class="skill.catId === active.id
                    ? 'border-[#A7EF9E]/50 text-[#A7EF9E] bg-[#A7EF9E]/5'
                    : 'border-white/8 text-white/20 hover:border-white/20 hover:text-white/40'"
                >
                  {{ skill.name }}
                </span>
              </div>
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