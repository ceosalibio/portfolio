<script setup>
import { ref } from "vue"
import { Mail, Github, Linkedin, Smartphone, X } from "lucide-vue-next"
import emailjs from "emailjs-com"

const showModal = ref(false)
const senderEmail = ref("")
const senderMessage = ref("")
const isLoading = ref(false)
const toast = ref({ show: false, message: "", type: "" })

const showToast = (msg, type = "success") => {
  toast.value = { show: true, message: msg, type }
  setTimeout(() => {
    toast.value.show = false
  }, 3000) // auto-hide after 3s
}

const contacts = [
  {
    name: "Email",
    icon: Mail,
    // label: "salibioarceo@gmail.com",
    url: "#", // we override this to open modal
    isEmail: true,
  },
  {
    name: "GitHub",
    icon: Github,
    // label: "github.com/ceosalibio",
    url: "https://github.com/ceosalibio",
  },
  {
    name: "LinkedIn",
    icon: Linkedin,
    // label: "linkedin.com/in/arceo-salibio-698457264",
    url: "https://www.linkedin.com/in/arceo-salibio-698457264/",
  },
  {
    name: "Phone",
    icon: Smartphone,
    label: "+639676087725",
    url: "tel:+639676087725",
  },
]

const handleSend = async () => {
  if (!senderEmail.value || !senderMessage.value) {
    alert("Please fill in all fields")
    return
  }
  isLoading.value = true
  // // Example: using mailto fallback
  // window.location.href = `mailto:salibioarceo@gmail.com?subject=Message from ${senderEmail.value}&body=${encodeURIComponent(senderMessage.value)}`
try {
    const result = await emailjs.send(
      "service_6dp8uzi",    // from EmailJS
      "template_v2cz81h",   // from EmailJS
      {
        from_email: senderEmail.value,
        message: senderMessage.value,
        subject: `Message from ${senderEmail.value}`,

      },
      "B8UAYEDc22zocLcq8"     // from EmailJS
    )

    console.log("Email sent:", result.text)
    // alert("Message sent successfully!")
    showToast("Message sent successfully!", "success")

    senderEmail.value = ""
    senderMessage.value = ""
    showModal.value = false
  } catch (err) {
    console.error("Failed to send email:", err)
    // alert("Error sending email. Try again later.")
  showToast("Error sending email. Try again later.", "error")
  } finally {
    isLoading.value = false // 👈 stop loading
  }

}
</script>

<template>
  <section class="py-16 animate-fadeIn">
    <div class="text-center mb-12 relative">
      <h2
        class="text-4xl font-extrabold text-transparent bg-clip-text bg-gradient-to-r from-cyan-400 to-blue-500"
      >
        Contact Me
      </h2>
      <p class="text-gray-400 mt-3 max-w-xl mx-auto">
        Interested in working together? Reach out through any platform below.
      </p>
      <div
        class="absolute left-1/2 -translate-x-1/2 top-0 w-32 h-32 bg-cyan-500/10 rounded-full blur-3xl animate-ping"
      ></div>
    </div>

    <div class="flex flex-wrap justify-center gap-8">
      <a
        v-for="c in contacts"
        :key="c.name"
        :href="c.isEmail ? null : c.url"
        :target="c.isEmail ? null : '_blank'"
        rel="noopener"
        class="relative w-44 h-44 bg-gray-900/50 backdrop-blur-md border border-gray-700 rounded-2xl
               flex flex-col items-center justify-center text-gray-300 transition
               hover:scale-110 hover:border-cyan-400 hover:shadow-cyan-500/50 hover:text-white
               shadow-lg hover:shadow-xl cursor-pointer"
        @click.prevent="c.isEmail ? (showModal = true) : null"
      >
        <div
          class="w-16 h-16 rounded-full flex items-center justify-center mb-3 bg-gradient-to-r from-cyan-400 to-blue-500 shadow-lg transition group-hover:shadow-cyan-400/60"
        >
          <component :is="c.icon" class="w-8 h-8 text-white" />
        </div>
        <span class="font-semibold text-sm">{{ c.name }}</span>
        <span class="text-xs text-gray-400 mt-1 break-all">{{ c.label }}</span>
      </a>
    </div>

    <!-- Modal -->
    <div
      v-if="showModal"
      class="fixed inset-0 flex items-center justify-center bg-black/60 backdrop-blur-sm z-50"
    >
      <div
        class="bg-gray-900 p-6 rounded-2xl w-full max-w-md border border-gray-700 relative"
      >
        <!-- Close Button -->
        <button
          class="absolute top-3 right-3 text-gray-400 hover:text-white"
          @click="showModal = false"
        >
          <X class="w-5 h-5" />
        </button>

        <h3 class="text-xl font-bold text-white mb-4">Send me an Email</h3>

        <div class="space-y-4">
          <input
            type="email"
            v-model="senderEmail"
            placeholder="Your email"
            class="w-full p-3 rounded-lg bg-gray-800 text-white border border-gray-700 focus:ring-2 focus:ring-cyan-400"
          />
          <textarea
            v-model="senderMessage"
            rows="4"
            placeholder="Your message"
            class="w-full p-3 rounded-lg bg-gray-800 text-white border border-gray-700 focus:ring-2 focus:ring-cyan-400"
          ></textarea>
          <button
            class="w-full py-3 rounded-lg bg-gradient-to-r from-cyan-400 to-blue-500 text-white font-semibold hover:opacity-90 transition flex items-center justify-center"
            :disabled="isLoading"
            @click="handleSend"
          >
            <span v-if="!isLoading">Send</span>
            <svg
              v-else
              class="animate-spin h-5 w-5 text-white"
              xmlns="http://www.w3.org/2000/svg"
              fill="none"
              viewBox="0 0 24 24"
            >
              <circle
                class="opacity-25"
                cx="12"
                cy="12"
                r="10"
                stroke="currentColor"
                stroke-width="4"
              ></circle>
              <path
                class="opacity-75"
                fill="currentColor"
                d="M4 12a8 8 0 018-8v4a4 4 0 00-4 4H4z"
              ></path>
            </svg>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>
