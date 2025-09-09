<script setup>
import { Mail, Github, Linkedin } from "lucide-vue-next"

const contacts = [
  {
    name: "Email",
    icon: Mail,
    url: "mailto:juan.delacruz@example.com", // replace with your real email
  },
  {
    name: "GitHub",
    icon: Github,
    url: "https://github.com/yourusername", // replace with your real github
  },
  {
    name: "LinkedIn",
    icon: Linkedin,
    url: "https://linkedin.com/in/yourusername", // replace with your real linkedin
  },
]
</script>

<template>
  <section class="py-16 text-center animate-fadeIn">
    <h2 class="text-3xl font-bold mb-8">Contact Me</h2>
    <p class="text-gray-400 mb-6">
      Interested in working together? Reach out through any platform below:
    </p>

    <div class="flex justify-center gap-8">
      <a
        v-for="c in contacts"
        :key="c.name"
        :href="c.url"
        target="_blank"
        rel="noopener"
        class="flex flex-col items-center text-gray-300 hover:text-white transition transform hover:scale-110"
      >
        <component :is="c.icon" class="w-8 h-8 mb-2" />
        <span class="text-sm">{{ c.name }}</span>
      </a>
    </div>
  </section>
</template>
