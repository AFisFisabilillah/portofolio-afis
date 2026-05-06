<script setup lang="ts">
const currentYear = new Date().getFullYear()

const footerLinks = [
  { label: 'Home', href: '#' },
  { label: 'About', href: '#about' },
  { label: 'Projects', href: '#projects' },
  { label: 'Skills', href: '#skills' },
  { label: 'Contact', href: '#contact' },
]

const socials = [
  { label: 'Github', href: 'https://github.com/AFisFisabilillah' },
  { label: 'Email', href: 'mailto:afisfisabillah@gmail.com' },
  { label: 'Linkedin', href: 'https://www.linkedin.com/in/afisfisabillah/' },
]
</script>

<template>
  <footer class="relative w-full overflow-hidden bg-black px-6 py-10 md:px-16">
    <div class="absolute left-0 top-0 h-px w-full bg-primary/15" />
    <div class="pixel-strip absolute left-0 top-0 h-px w-full opacity-70" />

    <div class="relative z-10 mx-auto max-w-6xl">
      <div class="grid grid-cols-1 gap-px bg-primary/10 border border-primary/10 md:grid-cols-[1fr_auto]">
        <div class="bg-black p-6 md:p-8">
          <div class="flex flex-col gap-6 md:flex-row md:items-center md:justify-between">
            <div>
              <div class="mb-4 flex items-center gap-2.5">
                <div class="relative flex size-10 items-center justify-center border border-primary bg-black">
                  <span class="font-['Bebas_Neue'] text-xl leading-none text-primary">A</span>
                  <span class="absolute -top-px -left-px size-1 bg-primary" />
                  <span class="absolute -top-px -right-px size-1 bg-primary" />
                  <span class="absolute -bottom-px -left-px size-1 bg-primary" />
                  <span class="absolute -bottom-px -right-px size-1 bg-primary" />
                </div>
                <div>
                  <p class="font-['Bebas_Neue'] text-2xl leading-none tracking-[0.12em] text-white">AFIS</p>
                  <p class="font-mono text-[9px] tracking-[0.2em] text-primary/60 uppercase">Fullstack Developer</p>
                </div>
              </div>

              <p class="max-w-md font-mono text-xs leading-[1.8] text-white/35">
                Portfolio pixel-themed untuk web, mobile, backend, dan produk digital yang siap dikembangkan.
              </p>
            </div>

            <div class="flex flex-col gap-4 md:items-end">
              <div class="flex items-center gap-2.5">
                <span class="relative flex size-2">
                  <span class="animate-ping absolute inline-flex h-full w-full bg-primary opacity-75" />
                  <span class="relative inline-flex size-2 bg-primary" />
                </span>
                <span class="font-mono text-[10px] tracking-[0.18em] text-primary uppercase">Open to work</span>
              </div>

              <div class="flex flex-wrap gap-2 md:justify-end">
                <a
                    v-for="social in socials"
                    :key="social.label"
                    :href="social.href"
                    class="border border-primary/20 px-3 py-1.5 font-mono text-[10px] font-bold tracking-[0.14em] uppercase text-white/35 transition-all duration-200 hover:border-primary hover:text-primary"
                >
                  {{ social.label }}
                </a>
              </div>
            </div>
          </div>
        </div>

        <nav class="grid grid-cols-2 gap-px bg-primary/10 sm:grid-cols-5 md:grid-cols-1 md:min-w-44">
          <a
              v-for="link in footerLinks"
              :key="link.label"
              :href="link.href"
              class="group relative bg-black px-5 py-4 font-mono text-[10px] font-bold tracking-[0.18em] uppercase text-white/35 transition-all duration-200 hover:bg-primary/[0.04] hover:text-primary"
          >
            <span class="absolute left-0 top-0 h-full w-0.5 bg-transparent transition-colors duration-200 group-hover:bg-primary" />
            {{ link.label }}
          </a>
        </nav>
      </div>

      <div class="mt-6 flex flex-col gap-4 border-t border-primary/10 pt-5 sm:flex-row sm:items-center sm:justify-between">
        <p class="font-mono text-[10px] tracking-[0.16em] text-white/20 uppercase">
          © {{ currentYear }} Afis Fisabillah
        </p>
        <div class="flex gap-px">
          <span
              v-for="i in 24"
              :key="i"
              class="h-1.5 w-3"
              :class="i % 5 === 0 ? 'bg-primary' : 'bg-primary/15'"
          />
        </div>
      </div>
    </div>
  </footer>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap');

.pixel-strip {
  background-image: repeating-linear-gradient(
      90deg,
      #A7EF9E 0,
      #A7EF9E 8px,
      transparent 8px,
      transparent 16px
  );
}
</style>
