<template>
  <section id="project" class="min-h-screen py-32 px-8 scroll-mt-24">
    <h2 class="text-4xl md:text-5xl font-bold text-center mb-20">
      Featured <span class="text-primary">Projects</span>
    </h2>

    <div class="grid md:grid-cols-2 lg:grid-cols-2 gap-12 max-w-6xl mx-auto">
      
      <div 
        v-for="project in projectList" 
        :key="project.title"
        class="group bg-card rounded-2xl overflow-hidden border border-white/5 hover:border-primary/50 transition-all duration-500 shadow-xl"
        data-aos="fade-up"
      >
        <div class="relative overflow-hidden aspect-video">
          <img 
            :src="project.image" 
            :alt="project.title"
            class="w-full h-full object-cover transition duration-500 group-hover:scale-110 opacity-80 group-hover:opacity-100"
          />
          <div class="absolute inset-0 bg-black/60 opacity-0 group-hover:opacity-100 transition-opacity duration-300 flex items-center justify-center gap-6">
            <a :href="project.github" target="_blank" class="p-3 bg-primary text-black rounded-full hover:scale-110 transition">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"></path></svg>
            </a>
            <a :href="project.demo" target="_blank" class="p-3 bg-white text-black rounded-full hover:scale-110 transition">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"></path><polyline points="15 3 21 3 21 9"></polyline><line x1="10" y1="14" x2="21" y2="3"></line></svg>
            </a>
          </div>
        </div>

        <div class="p-8">
          <h3 class="text-2xl font-bold mb-3 group-hover:text-primary transition-colors">
            {{ project.title }}
          </h3>
          <p class="text-gray-400 mb-6 leading-relaxed">
            {{ project.description }}
          </p>

          <div class="flex flex-wrap gap-2">
            <span 
              v-for="tech in project.tags" 
              :key="tech"
              class="text-xs font-semibold px-3 py-1 rounded-full border border-primary/30 bg-primary/5 text-primary"
            >
              {{ tech }}
            </span>
          </div>
        </div>
      </div>

    </div>
  </section>
</template>

<script setup>
const projectList = [
  {
    title: "Public Complaint Report",
    description: "A robust web-based application designed for efficient online complaint submission and tracking, streamlining communication between citizens and authorities.",
    image: "https://images.unsplash.com/photo-1510739859564-5879df1b994e?q=80&w=1000&auto=format&fit=crop", // Ganti dengan screenshot proyekmu
    tags: ["Bootstrap", "MySQL", "PHP"],
    github: "#",
    demo: "#"
  },
  {
    title: "AI-Powered Analysis Tool", // Contoh tambahan biar gak sepi
    description: "An experimental project using machine learning models to analyze data patterns and provide predictive insights for business decision making.",
    image: "https://images.unsplash.com/photo-1677442136019-21780ecad995?q=80&w=1000&auto=format&fit=crop", 
    tags: ["Python", "TensorFlow", "FastAPI"],
    github: "#",
    demo: "#"
  }
]
</script>