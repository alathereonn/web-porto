<template>
  <section id="home" class="relative min-h-screen flex flex-col justify-center items-center pt-20 pb-20 overflow-hidden">
    <div class="w-full max-w-6xl mx-auto px-6">
      <div class="flex flex-col md:flex-row items-center md:items-start gap-16 lg:gap-24">
        
        <!-- IMAGE -->
        <div class="relative w-52 h-52 md:w-80 md:h-80 flex-shrink-0 opacity-0 translate-y-10 animate-fadeUp">
          <div class="absolute inset-0 rounded-full bg-primary blur-3xl opacity-20 animate-pulseGlow"></div>
          <img 
            src="/profile.jpg"
            alt="Profile"
            class="relative w-full h-full object-cover 
                   [border-radius:60%_40%_30%_70%/60%_30%_70%_40%]
                   border-4 border-primary     
                   shadow-lg shadow-primary/30 
                   animate-float"
          />
        </div>

        <!-- TEXT -->
        <div class="text-justify md:ml-6 lg:ml-40 max-w-xl">

          <p class="text-lg text-gray-400">
            Hi, my name is
          </p>

          <h1 class="text-4xl md:text-6xl font-bold mt-2 leading-tight md:whitespace-nowrap">
            <span class="text-primary">{{ displayName }}</span>
            <span class="animate-pulse text-primary drop-shadow-[0_0_8px_var(--color-primary)]">|</span>
          </h1>

          <p class="mt-6 text-lg md:text-xl text-gray-400">
            Interested in 
            <span class="text-primary">{{ displayInterest }}</span>
            <span class="animate-pulse text-primary drop-shadow-[0_0_8px_var(--color-primary)]">|</span>
          </p>

          <p class="mt-6 text-gray-400 leading-relaxed">
            Third-year Computer Science student at Kalimantan Institute of Technology,
            passionate about building modern web applications,
            game systems, and AI-driven solutions.
          </p>

          <p class="mt-6 text-gray-400 leading-relaxed">
            Loves watching films and series (Breaking Bad, Better Call Saul,
            DC and Marvel Universe, etc.), playing games (God of War,
            Ghost of Tsushima, Souls games such as Elden Ring, etc.),
            and exploring new technologies.
          </p>

          <!-- PREMIUM BUTTON -->
          <div class="mt-8">
            <button 
              @click="scrollToAbout"
              class="group relative px-10 py-4 rounded-xl
                    font-semibold tracking-wide
                    border border-primary
                    text-primary
                    bg-transparent
                    transition-all duration-300
                    transform

                    shadow-[0_8px_0_0_var(--color-primary)]
                    
                    hover:bg-primary
                    hover:text-black
                    hover:-translate-y-1
                    hover:shadow-[0_12px_25px_var]

                    active:translate-y-2
                    active:shadow-[0_4px_0_0_var(--color-primary)]"
            >
              About Me
            </button>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const names = [
  "Zakaria Fattawari",
  "Alathereonn"
]

const interests = [
  "Web Development",
  "Game Development",
  "Computer Networks",
  "AI & Machine Learning"
]

const displayName = ref("")
const displayInterest = ref("")

const createTypingEffect = (texts, outputRef, typingSpeed = 100, deletingSpeed = 50, delay = 1000) => {
  let textIndex = 0
  let charIndex = 0
  let isDeleting = false

  const type = () => {
    const currentText = texts[textIndex]

    if (!isDeleting) {
      outputRef.value = currentText.substring(0, charIndex++)
      if (charIndex > currentText.length) {
        setTimeout(() => isDeleting = true, delay)
      }
    } else {
      outputRef.value = currentText.substring(0, charIndex--)
      if (charIndex < 0) {
        isDeleting = false
        textIndex = (textIndex + 1) % texts.length
      }
    }

    setTimeout(type, isDeleting ? deletingSpeed : typingSpeed)
  }

  type()
}

const scrollToAbout = () => {
  const target = document.getElementById('about')
  if (!target) return

  const start = window.pageYOffset
  // Gunakan -100 agar sama dengan navbar yang sudah diperbaiki
  const end = target.getBoundingClientRect().top + start - 100
  
  window.scrollTo({
    top: end,
    behavior: 'smooth'
  })
}

onMounted(() => {
  createTypingEffect(names, displayName, 150, 40, 1500)
  createTypingEffect(interests, displayInterest, 100, 50, 1000)
})
</script>