<script setup>
import BackgroundAnimation from './components/BackgroundAnimation.vue'
import HeroSection from './components/HeroSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import ExperienceSection from './components/ExperienceSection.vue'
import ProjectsSection from './components/ProjectsSection.vue'
import ContactSection from './components/ContactSection.vue'
</script>

<template>
  <main class="relative min-h-screen overflow-hidden">
    <!-- Global Background -->
    <div
      class="absolute inset-0 bg-gradient-to-r from-cyan-900 via-gray-900 to-blue-900 opacity-70 animate-gradient-x"
    ></div>

    <!-- Glow circles -->
    <div class="absolute w-[600px] h-[600px] bg-cyan-500/20 rounded-full blur-3xl top-32 left-10"></div>
    <div class="absolute w-[500px] h-[500px] bg-blue-500/20 rounded-full blur-3xl bottom-32 right-10"></div>

    <!-- Content -->
    <div class="relative z-10 max-w-6xl mx-auto px-4">
      <BackgroundAnimation />
      <HeroSection />
      <SkillsSection />
      <ExperienceSection />
      <ProjectsSection />
      <ContactSection />
    </div>
  </main>
</template>

<style>
@keyframes gradient-x {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}
.animate-gradient-x {
  background-size: 200% 200%;
  animation: gradient-x 10s ease infinite;
}
</style>

