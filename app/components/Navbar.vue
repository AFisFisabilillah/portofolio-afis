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
        ? 'max-w-3xl rounded-full border border-white/20 bg-white/70 px-5 py-3 shadow-lg shadow-black/10 backdrop-blur-md'
        : 'max-w-full rounded-none border border-transparent bg-transparent px-8 py-5 shadow-none'"
    >
      <div class="w-fit">
        <div class="flex size-10 items-center justify-center rounded-full bg-linear-to-r from-black to-gray-700">
          <p class="text-center text-xl font-bold text-white">A</p>
        </div>
      </div>

      <div class="hidden items-center gap-6 md:flex">
        <a
          v-for="menuItem in menuItems"
          :key="menuItem.label"
          :href="`${menuItem.link}`"
          class="text-sm font-medium text-gray-800 transition-colors hover:text-black"
        >
          {{ menuItem.label }}
        </a>
      </div>

      <button
        type="button"
        class="flex size-10 items-center justify-center rounded-full text-gray-900 transition-colors hover:bg-black/5 md:hidden"
        :aria-expanded="isMobileMenuOpen"
        aria-label="Toggle navigation menu"
        @click="isMobileMenuOpen = !isMobileMenuOpen"
      >
        <span class="relative block size-5">
          <span
            class="absolute left-0 top-1 block h-0.5 w-5 rounded-full bg-current transition-transform duration-300"
            :class="isMobileMenuOpen ? 'translate-y-2 rotate-45' : ''"
          />
          <span
            class="absolute left-0 top-2.5 block h-0.5 w-5 rounded-full bg-current transition-opacity duration-300"
            :class="isMobileMenuOpen ? 'opacity-0' : 'opacity-100'"
          />
          <span
            class="absolute left-0 top-4 block h-0.5 w-5 rounded-full bg-current transition-transform duration-300"
            :class="isMobileMenuOpen ? '-translate-y-1.5 -rotate-45' : ''"
          />
        </span>
      </button>
    </nav>

    <div
      class="mx-auto mt-3 overflow-hidden rounded-3xl border border-white/30 bg-white/85 shadow-lg shadow-black/10 backdrop-blur-md transition-all duration-300 md:hidden"
      :class="[
        isScrolled ? 'max-w-3xl' : 'mx-4',
        isMobileMenuOpen ? 'max-h-72 opacity-100' : 'max-h-0 border-transparent opacity-0'
      ]"
    >
      <div class="flex flex-col p-2">
        <a
          v-for="menuItem in menuItems"
          :key="`mobile-${menuItem.label}`"
          :href="menuItem.link"
          class="rounded-2xl px-4 py-3 text-sm font-medium text-gray-800 transition-colors hover:bg-black/5 hover:text-black"
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

</style>
