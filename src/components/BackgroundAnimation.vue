<script setup>
import { onMounted, ref } from "vue"

// Skill logos (you can replace with real SVGs or images in /public)
const skills = [
  { name: "Vue", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vuejs/vuejs-original.svg" },
  { name: "React", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" },
  { name: "Laravel", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/laravel/laravel-plain.svg" },
  { name: "Node.js", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg" },
  { name: "Docker", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg" },
//   { name: "AWS", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/amazonwebservices/amazonwebservices-original.svg" },
  { name: "MySQL", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg" },
  { name: "Firebase", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/firebase/firebase-plain.svg" },
  { name: "PHP", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg" },
  { name: "JavaScript", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" },
  { name: "CSS", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" },
  { name: "Tailwind", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/tailwindcss/tailwindcss-plain.svg" },
  { name: "Git", icon: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" },
]

const floatingIcons = ref([])

onMounted(() => {
  setInterval(() => {
    const skill = skills[Math.floor(Math.random() * skills.length)]
    const id = Date.now()

    floatingIcons.value.push({
      id,
      icon: skill.icon,
      left: Math.random() * 100, // random horizontal position
      size: Math.random() * 40 + 30, // 30–70px
      duration: Math.random() * 10 + 8 // fall speed
    })

    // remove after falling
    setTimeout(() => {
      floatingIcons.value = floatingIcons.value.filter(i => i.id !== id)
    }, 15000)
  }, 1200) // new icon every 1.2s
})
</script>

<template>
  <div class="fixed inset-0 -z-10 overflow-hidden pointer-events-none">
    <div
      v-for="icon in floatingIcons"
      :key="icon.id"
      class="absolute animate-fall"
      :style="{
        left: icon.left + '%',
        width: icon.size + 'px',
        height: icon.size + 'px',
        animationDuration: icon.duration + 's'
      }"
    >
      <img :src="icon.icon" class="w-full h-full object-contain opacity-70" />
    </div>
  </div>
</template>

<style scoped>
@keyframes fall {
  0% {
    transform: translateY(-100px) rotate(0deg);
    opacity: 0;
  }
  10% {
    opacity: 0.8;
  }
  100% {
    transform: translateY(110vh) rotate(360deg);
    opacity: 0;
  }
}

.animate-fall {
  animation-name: fall;
  animation-timing-function: linear;
}
</style>
