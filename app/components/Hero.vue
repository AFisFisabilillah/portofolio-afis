<script setup lang="ts">
</script>

<template>
  <div class="relative flex h-screen w-full items-center overflow-hidden bg-black px-6 sm:px-10 lg:px-20">

    <!-- PixelBlast full background -->
    <PixelBlast
        style="position:absolute; "
        variant="square"
        :pixel-size="5"
        color="#A7EF9E"
        :pattern-scale="4"
        :pattern-density="1.2"
        :pixel-size-jitter="0.7"
        :enable-ripples="true"
        :ripple-speed="0.4"
        :ripple-thickness="0.12"
        :ripple-intensity-scale="1.5"
        :speed="0.6"
        :transparent="true"
        :edge-fade="0.1"
    />

    <div class="absolute inset-0 z-[1] bg-black/55" />

    <div class="relative z-[2] flex w-full max-w-[900px] flex-col items-start text-left">

      <!-- Label row -->

      <h1 class="mb-2 flex flex-col items-start text-left leading-[0.88]">
        <span class="hero-outline text-left font-['Bebas_Neue'] text-9xl block animate-fade-up [animation-delay:50ms]">
          Afis
        </span>
        <span class="font-['Bebas_Neue'] text-9xl text-white block animate-fade-up [animation-delay:150ms]">
          Fisabillah
        </span>
      </h1>

      <p class="font-mono text-sm leading-[1.8] text-white/60 tracking-wide mb-4 animate-fade-up [animation-delay:300ms]">
        Membangun aplikasi web dan mobile yang modern, rapi, dan fungsional dengan fokus pada performa, struktur, dan pengalaman pengguna.
      </p>

      <a
          href="#"
          class="inline-flex items-center gap-2.5 bg-primary text-black font-mono text-[11px] font-bold tracking-[0.18em] uppercase px-6 py-3.5 border-2 border-primary transition-all duration-200 hover:bg-transparent hover:text-primary mb-12 animate-fade-up [animation-delay:380ms]"
      >
        <span>GET STARTED</span>
        <svg width="16" height="16" viewBox="0 0 16 16" fill="none">
          <path d="M3 8H13M13 8L8.5 3.5M13 8L8.5 12.5" stroke="currentColor" stroke-width="1.5" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </a>


    </div>
  </div>
</template>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Bebas+Neue&display=swap');

.hero-outline {
  -webkit-text-stroke: 2px #A7EF9E;
  color: transparent;
}

@keyframes fade-up {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.animate-fade-up {
  animation: fade-up 0.8s cubic-bezier(0.16, 1, 0.3, 1) both;
}
</style>
