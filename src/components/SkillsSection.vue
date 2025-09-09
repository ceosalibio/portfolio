<script setup>
const skills = [
  { name: "Vue", logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/vuejs/vuejs-original.svg" },
  { name: "React", logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/react/react-original.svg" },
  { name: "jQuery", logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/jquery/jquery-original.svg" },
  { name: "JavaScript", logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/javascript/javascript-original.svg" },
  { name: "PHP", logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/php/php-original.svg" },
  { name: "CSS", logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/css3/css3-original.svg" },
  { name: "Tailwind", logo: "https://www.vectorlogo.zone/logos/tailwindcss/tailwindcss-icon.svg" },
  { name: "Laravel", logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/laravel/laravel-plain.svg" },
  { name: "Node.js", logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/nodejs/nodejs-original.svg" },
  { name: "Firebase", logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/firebase/firebase-plain.svg" },
  { name: "AWS Lambda", logo: "https://www.vectorlogo.zone/logos/amazon_aws-lambda/amazon_aws-lambda-icon.svg" },
  { name: "AWS S3", logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/amazonwebservices/amazonwebservices-original.svg" },
  { name: "MySQL", logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mysql/mysql-original.svg" },
  { name: "NoSQL", logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/mongodb/mongodb-original.svg" },
  { name: "Docker", logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/docker/docker-original.svg" },
  { name: "Git", logo: "https://cdn.jsdelivr.net/gh/devicons/devicon/icons/git/git-original.svg" },
  { name: "API Integration", logo: "https://cdn-icons-png.flaticon.com/512/1006/1006363.png" },
]
</script>

<template>
  <section class="py-16 animate-fadeIn">
    <h2 class="text-3xl font-bold mb-12 text-center text-cyan-400 tracking-wide">
      Skills
    </h2>
    <div class="grid grid-cols-2 sm:grid-cols-3 md:grid-cols-4 lg:grid-cols-6 gap-6 place-items-center">
      <div
        v-for="skill in skills"
        :key="skill.name"
        class="w-28 h-28 bg-gradient-to-br from-gray-800 to-gray-900 
               rounded-xl shadow-lg shadow-black/50 border border-gray-700
               flex flex-col items-center justify-center 
               transition transform hover:scale-110 hover:border-cyan-400
               hover:shadow-cyan-500/40 group relative overflow-hidden"
      >
        <!-- bevel/glass overlay -->
        <div class="absolute inset-0 bg-gradient-to-br from-white/10 to-transparent opacity-10 group-hover:opacity-20"></div>

        <img :src="skill.logo" :alt="skill.name" class="w-12 h-12 mb-2 relative z-10" />
        <span class="text-sm text-gray-300 group-hover:text-cyan-400 relative z-10">
          {{ skill.name }}
        </span>
      </div>
    </div>
  </section>
</template>
