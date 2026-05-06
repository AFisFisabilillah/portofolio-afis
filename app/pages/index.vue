<script setup lang="ts">

import Navbar from "~/components/Navbar.vue";
import About from "~/components/About.vue";
import Experience from "~/components/Experience.vue";
import Projects from "~/components/Projects.vue";
import Skills from "~/components/Skills.vue";
import Contact from "~/components/Contact.vue";
</script>

<template>
  <div class="min-h-screen ">
    <Navbar></Navbar>
    <Hero/>
    <About/>
    <Experience/>
    <Projects/>
    <Skills/>
    <Contact/>
  </div>
</template>

<style scoped>

</style>
