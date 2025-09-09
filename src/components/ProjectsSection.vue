<script setup>
const projects = [
  {
    name: "Inventory System",
    description: "A system to manage stocks and products efficiently with reports and tracking.",
    icon: "📦",
  },
  {
    name: "Government System",
    description: "A secure platform built to streamline government workflows and citizen services.",
    icon: "🏛️",
  },
  {
    name: "Booking System",
    description: "An online booking and reservation system with calendar integration.",
    icon: "📅",
  },
]
</script>

<template>
  <section class="py-20 animate-fadeIn relative">
    <h2
      class="text-4xl font-extrabold mb-16 text-center bg-gradient-to-r from-cyan-400 to-blue-500 bg-clip-text text-transparent"
    >
      Projects
    </h2>

    <div class="grid md:grid-cols-3 gap-8">
      <div
        v-for="project in projects"
        :key="project.name"
        class="relative group bg-gradient-to-br from-gray-800/80 to-gray-900/80 
               rounded-2xl border border-gray-700 overflow-hidden
               shadow-xl transition transform hover:-translate-y-2 hover:shadow-cyan-500/30"
      >
        <!-- Glow effect on hover -->
        <div
          class="absolute inset-0 bg-gradient-to-tr from-cyan-500/20 to-blue-500/20 opacity-0 group-hover:opacity-100 transition"
        ></div>

        <!-- Content -->
        <div class="relative p-8 flex flex-col items-center text-center">
          <div
            class="w-16 h-16 flex items-center justify-center text-3xl rounded-full 
                   bg-gray-700 group-hover:bg-cyan-500/20 transition mb-4"
          >
            {{ project.icon }}
          </div>
          <h3 class="font-bold text-xl text-white group-hover:text-cyan-400 transition">
            {{ project.name }}
          </h3>
          <p class="text-gray-400 mt-3 text-sm">
            {{ project.description }}
          </p>
        </div>
      </div>
    </div>
  </section>
</template>
