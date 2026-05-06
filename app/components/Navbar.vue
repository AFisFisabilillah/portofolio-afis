<script setup lang="ts">
const isScrolled = ref(false)
const isMobileMenuOpen = ref(false)
const menuItems = [
  { label: 'Home', ariaLabel: 'Go to home page', link: '#' },
  { label: 'About', ariaLabel: 'Learn about us', link: '#about' },
  { label: 'Services', ariaLabel: 'View our services', link: '#services' },
  { label: 'Contact', ariaLabel: 'Get in touch', link: '#contact' }
]
const handleScroll = () => {
  isScrolled.value = window.scrollY > 12
}
const closeMobileMenu = () => {
  isMobileMenuOpen.value = false
}
onMounted(() => {
  handleScroll()
  window.addEventListener('scroll', handleScroll, { passive: true })
})
onBeforeUnmount(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<template>
  <header
      class="fixed left-0 top-0 z-50 w-full transition-all duration-300 ease-out"
      :class="isScrolled ? 'px-4 pt-4' : 'px-0 pt-0'"
  >
    <nav
        class="mx-auto flex items-center justify-between transition-all duration-300 ease-out"
        :class="isScrolled
        ? 'max-w-3xl rounded-none border border-[#A7EF9E]/30 bg-black/60 px-5 py-3 shadow-lg shadow-[#A7EF9E]/5 backdrop-blur-md navbar-scrolled'
        : 'max-w-full rounded-none border-b border-[#A7EF9E]/10 bg-transparent px-8 py-5'"
    >
      <!-- Logo -->
      <div class="flex items-center gap-2.5">
        <div class="logo-box relative flex size-9 items-center justify-center border border-[#A7EF9E] bg-black">
          <span class="font-['Bebas_Neue'] text-lg text-[#A7EF9E] leading-none">A</span>
          <!-- corner pixels -->
          <span class="absolute -top-px -left-px size-1 bg-[#A7EF9E]" />
          <span class="absolute -top-px -right-px size-1 bg-[#A7EF9E]" />
          <span class="absolute -bottom-px -left-px size-1 bg-[#A7EF9E]" />
          <span class="absolute -bottom-px -right-px size-1 bg-[#A7EF9E]" />
        </div>
        <span class="font-['Bebas_Neue'] text-lg tracking-[0.15em] text-white">ACME</span>
      </div>

      <!-- Desktop menu -->
      <div class="hidden items-center gap-8 md:flex">
        <a
            v-for="menuItem in menuItems"
            :key="menuItem.label"
            :href="menuItem.link"
            class="nav-link font-mono text-[11px] font-bold tracking-[0.18em] uppercase text-white/50 transition-colors duration-200 hover:text-[#A7EF9E]"
        >
          {{ menuItem.label }}
        </a>
      </div>

      <div class="flex items-center gap-4">
        <a
            href="#"
            class="hidden md:inline-flex items-center gap-2 border border-[#A7EF9E] px-4 py-1.5 font-mono text-[10px] font-bold tracking-[0.18em] uppercase text-[#A7EF9E] transition-all duration-200 hover:bg-[#A7EF9E] hover:text-black"
        >
          CONTAC
        </a>

        <!-- Hamburger -->
        <button
            type="button"
            class="flex size-9 items-center justify-center border border-[#A7EF9E]/30 text-white transition-colors hover:border-[#A7EF9E] hover:text-[#A7EF9E] md:hidden"
            :aria-expanded="isMobileMenuOpen"
            aria-label="Toggle navigation menu"
            @click="isMobileMenuOpen = !isMobileMenuOpen"
        >
          <span class="relative block size-4">
            <span
                class="absolute left-0 top-0.5 block h-px w-4 bg-current transition-transform duration-300"
                :class="isMobileMenuOpen ? 'translate-y-1.5 rotate-45' : ''"
            />
            <span
                class="absolute left-0 top-2 block h-px w-4 bg-current transition-opacity duration-300"
                :class="isMobileMenuOpen ? 'opacity-0' : 'opacity-100'"
            />
            <span
                class="absolute left-0 top-3.5 block h-px w-4 bg-current transition-transform duration-300"
                :class="isMobileMenuOpen ? '-translate-y-1.5 -rotate-45' : ''"
            />
          </span>
        </button>
      </div>
    </nav>

    <!-- Handphone -->
    <div
        class="mx-4 overflow-hidden border border-[#A7EF9E]/20 bg-black/90 backdrop-blur-md transition-all duration-300 md:hidden"
        :class="isMobileMenuOpen ? 'max-h-72 opacity-100' : 'max-h-0 border-transparent opacity-0'"
    >
      <div class="flex flex-col py-2">
        <a
            v-for="menuItem in menuItems"
            :key="`mobile-${menuItem.label}`"
            :href="menuItem.link"
            class="px-6 py-3 font-mono text-[11px] font-bold tracking-[0.18em] uppercase text-white/50 transition-colors hover:bg-[#A7EF9E]/5 hover:text-[#A7EF9E]"
            :aria-label="menuItem.ariaLabel"
            @click="closeMobileMenu"
        >
          {{ menuItem.label }}
        </a>
      </div>
    </div>
  </header>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap');

.navbar-scrolled {
  box-shadow: 0 0 24px 0 rgba(167, 239, 158, 0.06), 0 1px 0 0 rgba(167, 239, 158, 0.12);
}

.nav-link {
  position: relative;
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: -3px;
  left: 0;
  width: 0;
  height: 1px;
  background: #A7EF9E;
  transition: width 0.2s ease;
}

.nav-link:hover::after {
  width: 100%;
}
</style>