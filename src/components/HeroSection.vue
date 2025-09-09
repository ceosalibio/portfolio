<script setup>
import { ref, onMounted } from "vue"

const titles = [
  "Full-Stack Web Developer",
  "Vue Specialist",
  "Laravel & Node.js Expert",
  "Cloud & API Integrator"
]

const quotes = [
  "Turning complex problems into elegant web solutions.",
  "Code is like humor — when you have to explain it, it’s bad.",
  "Building scalable systems with creativity and precision.",
  "Transforming ideas into impactful digital experiences."
]

const currentTitle = ref("")
const currentQuote = ref(quotes[0])

let titleIndex = 0
let charIndex = 0
let deleting = false
let quoteIndex = 0

onMounted(() => {
  // Typewriter effect for titles
  function typeEffect() {
    if (!deleting && charIndex <= titles[titleIndex].length) {
      currentTitle.value = titles[titleIndex].substring(0, charIndex++)
    } else if (deleting && charIndex >= 0) {
      currentTitle.value = titles[titleIndex].substring(0, charIndex--)
    }

    if (charIndex === titles[titleIndex].length + 1) {
      deleting = true
      setTimeout(typeEffect, 1000)
      return
    }

    if (charIndex < 0) {
      deleting = false
      titleIndex = (titleIndex + 1) % titles.length
    }

    setTimeout(typeEffect, deleting ? 50 : 120)
  }

  // Rotate quotes every 5s
  setInterval(() => {
    quoteIndex = (quoteIndex + 1) % quotes.length
    currentQuote.value = quotes[quoteIndex]
  }, 5000)

  typeEffect()
})
</script>

<template>
  <section
    class="relative flex flex-col items-center justify-center h-screen text-center overflow-hidden"
  >
    <!-- Background gradient animation -->
    <div
      class="  bg-gradient-to-r from-cyan-900 via-gray-900 to-blue-900 opacity-70 animate-gradient-x"
    ></div>

    <!-- Glow circles -->
    <div class="absolute w-[500px] h-[500px] bg-cyan-500/20 rounded-full blur-3xl top-20 left-10"></div>
    <div class="absolute w-[400px] h-[400px] bg-blue-500/20 rounded-full blur-3xl bottom-20 right-10"></div>

    <!-- Content -->
    <div class="relative z-10">
      <h1
        class="text-6xl md:text-7xl font-extrabold bg-gradient-to-r from-cyan-400 to-blue-500 bg-clip-text text-transparent animate-fadeIn drop-shadow-lg"
      >
        Arceo Jr. S. Salibio
      </h1>

      <p
        class="text-2xl md:text-3xl mt-6 h-10 text-cyan-300 font-mono tracking-wide"
      >
        {{ currentTitle
        }}<span class="text-cyan-400 animate-ping inline-block w-2">|</span>
      </p>

      <p
        key="quote"
        class="mt-8 text-lg md:text-xl text-gray-300 italic max-w-2xl mx-auto transition-opacity duration-700"
      >
        "{{ currentQuote }}"
      </p>
    </div>
  </section>
</template>

<style scoped>

</style>
