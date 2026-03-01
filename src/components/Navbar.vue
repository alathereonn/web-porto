<template>
  <nav class="fixed w-full bg-darkbg/90 backdrop-blur-md z-50 shadow-lg">
    <div class="flex flex-col md:flex-row justify-between items-center max-w-7xl mx-auto px-8 py-10 w-full gap-4 md:gap-8">
      <h1 class="text-xl font-bold text-primary cursor-pointer" @click="scrollTo('home')">
        ALATHEREONN</h1>

      <div class="hidden md:flex gap-8">
        <button
          v-for="section in sections"
          :key="section"
          @click="scrollTo(section)"
          :class="[
            'transition hover:text-primary capitalize',
            active === section ? 'text-primary' : ''
          ]"
        >
          {{ section }}
        </button>
      </div>

    </div>
  </nav>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const sections = ['home','about','qualification','project','contact']
const active = ref('home')

const scrollTo = (id, duration = 500) => {
  active.value = id // langsung update warna saat diklik

  const target = document.getElementById(id)
  if (!target) return

  const start = window.pageYOffset
  const end = target.getBoundingClientRect().top + start - 100
  const distance = end - start
  let startTime = null

  const animation = (currentTime) => {
    if (!startTime) startTime = currentTime
    const timeElapsed = currentTime - startTime
    const progress = Math.min(timeElapsed / duration, 1)

    window.scrollTo(0, start + distance * easeInOut(progress))

    if (timeElapsed < duration) {
      requestAnimationFrame(animation)
    }
  }

  const easeInOut = (t) => {
    return t < 0.5
      ? 2 * t * t
      : 1 - Math.pow(-2 * t + 2, 2) / 2
  }

  requestAnimationFrame(animation)
}

onMounted(() => {
  window.addEventListener('scroll', () => {
    sections.forEach(section => {
      const el = document.getElementById(section)
      if (el) {
        const top = window.scrollY
        const offset = el.offsetTop - 150
        const height = el.offsetHeight

        if (top >= offset && top < offset + height) {
          active.value = section
        }
      }
    })
  })
})
</script>