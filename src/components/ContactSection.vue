<script setup>
import { Mail, Github, Linkedin, Smartphone } from "lucide-vue-next"

const contacts = [
  {
    name: "Email",
    icon: Mail,
    label: "salibioarceo@gmail.com",
    url: "mailto:salibioarceo@gmail.com",
  },
  {
    name: "GitHub",
    icon: Github,
    label: "github.com/ceosalibio",
    url: "https://github.com/ceosalibio",
  },
  {
    name: "LinkedIn",
    icon: Linkedin,
    label: "linkedin.com/in/arceo-salibio-698457264",
    url: "https://www.linkedin.com/in/arceo-salibio-698457264/",
  },
  {
    name: "Phone",
    icon: Smartphone,
    label: "+639676087725",
    url: "tel:+639676087725",
  },
]
</script>

<template>
  <section class="py-16 animate-fadeIn">
    <div class="text-center mb-12 relative">
      <h2 class="text-4xl font-extrabold text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 to-blue-500">
        Contact Me
      </h2>
      <p class="text-gray-400 mt-3 max-w-xl mx-auto">
        Interested in working together? Reach out through any platform below.
      </p>
      <!-- Glowing accent circle -->
      <div class="absolute left-1/2 -translate-x-1/2 top-0 w-32 h-32 bg-cyan-500/10 rounded-full blur-3xl animate-ping"></div>
    </div>

    <div class="flex flex-wrap justify-center gap-8">
      <a
        v-for="c in contacts"
        :key="c.name"
        :href="c.url"
        target="_blank"
        rel="noopener"
        class="relative w-44 h-44 bg-gray-900/50 backdrop-blur-md border border-gray-700 rounded-2xl
               flex flex-col items-center justify-center text-gray-300 transition
               hover:scale-110 hover:border-cyan-400 hover:shadow-cyan-500/50 hover:text-white
               shadow-lg hover:shadow-xl"
      >
        <!-- Neon icon circle -->
        <div
          class="w-16 h-16 rounded-full flex items-center justify-center mb-3 bg-gradient-to-r from-cyan-400 to-blue-500 shadow-lg transition group-hover:shadow-cyan-400/60"
        >
          <component :is="c.icon" class="w-8 h-8 text-white" />
        </div>
        <span class="font-semibold text-sm">{{ c.name }}</span>
        <span class="text-xs text-gray-400 mt-1 break-all">{{ c.label }}</span>
      </a>
    </div>
  </section>
</template>
