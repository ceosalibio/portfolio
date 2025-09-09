<template>
  <section class="py-20 animate-fadeIn relative">
    <h2 class="text-3xl font-bold mb-16 text-center text-cyan-400 tracking-wide">
      Experience
    </h2>

    <!-- Timeline line -->
    <div class="absolute left-1/2 transform -translate-x-1/2 w-1 bg-gray-700 h-80"></div>

    <div class="space-y-12 relative z-10">
      <!-- Job 1: Web Developer (latest first) -->
      <div class="flex items-center w-full">
        <div class="w-1/2 pr-8 text-right">
          <h3 class="font-semibold text-xl text-white">Web Developer</h3>
          <p class="text-gray-400">2018 - Present</p>
        </div>

        <!-- Dot -->
        <div class="relative">
          <div
            class="w-6 h-6 bg-cyan-500 rounded-full border-4 border-gray-900 shadow-lg flex items-center justify-center"
          >
            💻
          </div>
        </div>

        <div class="w-1/2 pl-8">
          <div
            class="bg-gray-800 p-6 rounded-xl shadow-lg border border-gray-700 hover:border-cyan-400 hover:shadow-cyan-500/30 transition"
          >
            <p class="text-gray-300">
              Developing full-stack web applications with Vue, Laravel, Node.js, and AWS —
              delivering scalable, high-quality solutions.
            </p>
          </div>
        </div>
      </div>

      <!-- Job 2: Encoder -->
      <div class="flex items-center w-full">
        <div class="w-1/2 pr-8 text-right">
          <h3 class="font-semibold text-xl text-white">Encoder - HRD Singapore</h3>
          <p class="text-gray-400">June 2013 - March 2018</p>
        </div>

        <!-- Dot -->
        <div class="relative">
          <div
            class="w-6 h-6 bg-cyan-500 rounded-full border-4 border-gray-900 shadow-lg flex items-center justify-center"
          >
            🗂️
          </div>
        </div>

        <div class="w-1/2 pl-8">
          <div
            class="bg-gray-800 p-6 rounded-xl shadow-lg border border-gray-700 hover:border-cyan-400 hover:shadow-cyan-500/30 transition"
          >
            <p class="text-gray-300">
              Managed document encoding and data processing with precision to support HR operations.
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>
