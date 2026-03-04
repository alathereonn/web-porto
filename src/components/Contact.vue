<template>
  <section id="contact" class="relative min-h-screen flex flex-col items-center py-20 md:py-32 px-4 md:px-8 scroll-mt-24 overflow-hidden bg-darkbg">
    
    <div class="absolute inset-0 pointer-events-none opacity-20">
      <div class="absolute top-0 left-1/4 w-[40rem] h-[40rem] bg-primary/20 blur-[120px] rounded-full mix-blend-screen"></div>
      <div class="absolute bottom-0 right-1/4 w-[30rem] h-[30rem] bg-red-900/10 blur-[100px] rounded-full mix-blend-screen"></div>
    </div>

    <div class="relative z-10 w-full max-w-7xl text-center mb-12 md:mb-20">
      <h2 class="text-4xl md:text-5xl font-bold mb-4 text-white">
        Interested? <span class="text-primary">Call Me!</span>
      </h2>
      <div class="w-24 h-1 bg-primary mx-auto mb-6 shadow-[0_0_10px_var(--color-primary)]"></div>
      <p class="text-gray-400 text-sm md:text-lg max-w-2xl mx-auto leading-relaxed">
        Send your signal through the digital network. Let's collaborate to build the digital future together.
      </p>
    </div>

    <div class="relative z-10 w-full max-w-7xl grid grid-cols-1 lg:grid-cols-12 gap-6 md:gap-8 mb-24">
      
      <div class="lg:col-span-7 flex flex-col gap-6 md:gap-8">
        
        <div class="bg-card backdrop-blur-md border border-white/5 hover:border-primary/50 transition-all duration-500 p-6 md:p-10 rounded-2xl shadow-2xl relative overflow-hidden group flex flex-col flex-1">
          <div class="absolute top-0 left-0 w-1 h-full bg-primary/0 group-hover:bg-primary transition-all duration-500"></div>
          <h3 class="text-xl font-bold text-primary mb-6">Send a Message</h3>
          
          <form @submit.prevent="sendMessage" class="flex flex-col h-full gap-6">
            <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
              <div>
                <label class="flex items-center gap-2 text-sm text-gray-400 mb-2">
                  <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M20 21v-2a4 4 0 0 0-4-4H8a4 4 0 0 0-4 4v2"></path><circle cx="12" cy="7" r="4"></circle></svg>
                  Name
                </label>
                <input type="text" required placeholder="John Doe" class="w-full bg-darkbg border border-white/10 rounded-xl px-5 py-4 text-gray-200 placeholder-gray-600 focus:outline-none focus:border-primary focus:ring-1 focus:ring-primary transition-all text-base">
              </div>

              <div>
                <label class="flex items-center gap-2 text-sm text-gray-400 mb-2">
                  <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M4 4h16c1.1 0 2 .9 2 2v12c0 1.1-.9 2-2 2H4c-1.1 0-2-.9-2-2V6c0-1.1.9-2 2-2z"></path><polyline points="22,6 12,13 2,6"></polyline></svg>
                  Email
                </label>
                <input type="email" required placeholder="john@example.com" class="w-full bg-darkbg border border-white/10 rounded-xl px-5 py-4 text-gray-200 placeholder-gray-600 focus:outline-none focus:border-primary focus:ring-1 focus:ring-primary transition-all text-base">
              </div>
            </div>

            <div class="flex-1 flex flex-col">
              <label class="flex items-center gap-2 text-sm text-gray-400 mb-2">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M21 15a2 2 0 0 1-2 2H7l-4 4V5a2 2 0 0 1 2-2h14a2 2 0 0 1 2 2z"></path></svg>
                Message
              </label>
              <textarea required rows="6" placeholder="Describe your project or collaboration idea..." class="w-full flex-1 bg-darkbg border border-white/10 rounded-xl px-5 py-4 text-gray-200 placeholder-gray-600 focus:outline-none focus:border-primary focus:ring-1 focus:ring-primary transition-all text-base resize-none"></textarea>
            </div>

            <button type="submit" class="w-full mt-4 group relative px-8 py-4 rounded-xl font-bold tracking-wide text-base border border-primary text-primary bg-transparent hover:bg-primary hover:text-black transition-all duration-300 flex justify-center items-center gap-3 shadow-[0_6px_0_0_var(--color-primary)] hover:translate-y-1 hover:shadow-none active:translate-y-2">
              <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="group-hover:-translate-y-1 group-hover:translate-x-1 transition-transform"><line x1="22" y1="2" x2="11" y2="13"></line><polygon points="22 2 15 22 11 13 2 9 22 2"></polygon></svg>
              Send Message
            </button>
          </form>
        </div>

        <div class="bg-card backdrop-blur-md border border-white/5 hover:border-primary/50 transition-all duration-500 p-6 md:p-8 rounded-2xl shadow-xl relative overflow-hidden group">
          <div class="absolute top-0 left-0 w-1 h-full bg-primary/0 group-hover:bg-primary transition-all duration-500"></div>
          <h3 class="text-xl font-bold text-primary mb-6">Social Networks</h3>
          
          <div class="flex flex-wrap gap-4">
            <a href="https://github.com/alathereonn" target="_blank" class="p-4 bg-darkbg rounded-xl text-gray-400 hover:bg-white hover:text-black transition-all duration-300 hover:scale-105 hover:shadow-[0_5px_15px_rgba(190,24,93,0.4)] border border-white/5 hover:border-transparent">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M9 19c-5 1.5-5-2.5-7-3m14 6v-3.87a3.37 3.37 0 0 0-.94-2.61c3.14-.35 6.44-1.54 6.44-7A5.44 5.44 0 0 0 20 4.77 5.07 5.07 0 0 0 19.91 1S18.73.65 16 2.48a13.38 13.38 0 0 0-7 0C6.27.65 5.09 1 5.09 1A5.07 5.07 0 0 0 5 4.77a5.44 5.44 0 0 0-1.5 3.78c0 5.42 3.3 6.61 6.44 7A3.37 3.37 0 0 0 9 18.13V22"></path></svg>
            </a>
            <a href="https://www.linkedin.com/in/zakaria-fattawari" target="_blank" class="p-4 bg-darkbg rounded-xl text-gray-400 hover:bg-[#0A66C2] hover:text-white transition-all duration-300 hover:scale-105 hover:shadow-[0_5px_15px_rgba(10,102,194,0.4)] border border-white/5 hover:border-transparent">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M16 8a6 6 0 0 1 6 6v7h-4v-7a2 2 0 0 0-2-2 2 2 0 0 0-2 2v7h-4v-7a6 6 0 0 1 6-6z"></path><rect x="2" y="9" width="4" height="12"></rect><circle cx="4" cy="4" r="2"></circle></svg>
            </a>
            <a href="https://instagram.com/alathereonn_" target="_blank" class="p-4 bg-darkbg rounded-xl text-gray-400 hover:bg-[#E1306C] hover:text-white transition-all duration-300 hover:scale-105 hover:shadow-[0_5px_15px_rgba(225,48,108,0.4)] border border-white/5 hover:border-transparent">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="2" width="20" height="20" rx="5" ry="5"></rect><path d="M16 11.37A4 4 0 1 1 12.63 8 4 4 0 0 1 16 11.37z"></path><line x1="17.5" y1="6.5" x2="17.51" y2="6.5"></line></svg>
            </a>
            <a href="https://web.facebook.com/profile.php?id=100055464836367" target="_blank" class="p-4 bg-darkbg rounded-xl text-gray-400 hover:bg-[#1877F2] hover:text-white transition-all duration-300 hover:scale-105 hover:shadow-[0_5px_15px_rgba(24,119,242,0.4)] border border-white/5 hover:border-transparent">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M18 2h-3a5 5 0 0 0-5 5v3H7v4h3v8h4v-8h3l1-4h-4V7a1 1 0 0 1 1-1h3z"></path></svg>
            </a>
            <a href="https://steamcommunity.com/id/alathereonn/" target="_blank" class="p-4 bg-darkbg rounded-xl text-gray-400 hover:bg-[#2a475e] hover:text-white transition-all duration-300 hover:scale-105 hover:shadow-[0_5px_15px_rgba(102,192,244,0.4)] border border-white/5 hover:border-transparent">
              <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round">
                <path d="M16.5 5a4.5 4.5 0 1 1 -.653 8.953l-4.347 3.009l0 .038a3 3 0 0 1 -2.824 2.995l-.176 .005a3 3 0 0 1 -2.94 -2.402l-2.56 -1.098v-3.5l3.51 1.755a2.989 2.989 0 0 1 2.834 -.635l2.727 -3.546a4.5 4.5 0 0 1 4.429 -5.572z"></path>
                  <circle cx="16.5" cy="9.5" r="1">
                  </circle>
              </svg>
            </a>
          </div>
        </div>

      </div>

      <div class="lg:col-span-5 flex flex-col gap-6 md:gap-8">
        
        <div class="bg-card backdrop-blur-md border border-white/5 hover:border-primary/50 transition-all duration-500 p-6 md:p-8 rounded-2xl shadow-xl relative overflow-hidden group">
          <div class="absolute top-0 right-0 w-1 h-full bg-primary/0 group-hover:bg-primary transition-all duration-500"></div>
          <h3 class="text-xl font-bold text-primary mb-6">Contact Protocols</h3>
          
          <div class="space-y-6">
            <a href="mailto:zakriafattawari@gmail.com" class="flex items-center gap-5 group/item">
              <div class="p-4 bg-primary/10 text-primary rounded-xl group-hover/item:bg-primary group-hover/item:text-black transition-colors duration-300">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><rect x="2" y="4" width="20" height="16" rx="2" ry="2"></rect><path d="m22 7-8.97 5.7a1.94 1.94 0 0 1-2.06 0L2 7"></path></svg>
              </div>
              <div>
                <p class="text-sm text-gray-500 mb-1">Email Address</p>
                <p class="text-gray-200 group-hover/item:text-primary transition-colors text-base md:text-lg font-medium break-all">zakriafattawari@gmail.com</p>
              </div>
            </a>
            
            <a href="https://wa.me/6281288814966" target="_blank" class="flex items-center gap-5 group/item">
              <div class="p-4 bg-primary/10 text-primary rounded-xl group-hover/item:bg-primary group-hover/item:text-black transition-colors duration-300">
                <svg xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M22 16.92v3a2 2 0 0 1-2.18 2 19.79 19.79 0 0 1-8.63-3.07 19.5 19.5 0 0 1-6-6 19.79 19.79 0 0 1-3.07-8.67A2 2 0 0 1 4.11 2h3a2 2 0 0 1 2 1.72 12.84 12.84 0 0 0 .7 2.81 2 2 0 0 1-.45 2.11L8.09 9.91a16 16 0 0 0 6 6l1.27-1.27a2 2 0 0 1 2.11-.45 12.84 12.84 0 0 0 2.81.7A2 2 0 0 1 22 16.92z"></path></svg>
              </div>
              <div>
                <p class="text-sm text-gray-500 mb-1">WhatsApp</p>
                <p class="text-gray-200 group-hover/item:text-primary transition-colors text-base md:text-lg font-medium">+62 856-5114-9430</p>
              </div>
            </a>
          </div>
        </div>

        <div class="bg-card backdrop-blur-md border border-white/5 hover:border-primary/50 transition-all duration-500 rounded-2xl shadow-xl relative overflow-hidden group flex flex-col p-6 md:p-8 flex-1 min-h-[350px]">
          <div class="absolute top-0 right-0 w-1 h-full bg-primary/0 group-hover:bg-primary transition-all duration-500 z-10 pointer-events-none"></div>
          
          <div class="flex justify-between items-center mb-6">
            <h3 class="text-xl font-bold text-primary flex items-center gap-2">
              <svg xmlns="http://www.w3.org/2000/svg" width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><path d="M9 18V5l12-2v13"></path><circle cx="6" cy="18" r="3"></circle><circle cx="18" cy="16" r="3"></circle></svg>
              My Playlists
            </h3>
            <div class="flex gap-2">
              <button @click="prevPlaylist" class="p-1.5 bg-darkbg rounded-lg hover:text-primary hover:bg-white/10 transition-all border border-white/5">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="15 18 9 12 15 6"></polyline></svg>
              </button>
              <button @click="nextPlaylist" class="p-1.5 bg-darkbg rounded-lg hover:text-primary hover:bg-white/10 transition-all border border-white/5">
                <svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><polyline points="9 18 15 12 9 6"></polyline></svg>
              </button>
            </div>
          </div>

          <div ref="playlistSliderRef" class="flex overflow-x-auto snap-x snap-mandatory hide-scrollbar flex-1 rounded-xl scroll-smooth gap-6 md:gap-8">
            
            <div 
              v-for="(item, index) in myPlaylists" 
              :key="item.id" 
              class="w-full flex-shrink-0 snap-center relative bg-darkbg overflow-hidden border border-white/5 aspect-square md:aspect-auto rounded-xl flex flex-col"
            >
              
              <div 
                v-if="playingIndex !== index" 
                class="absolute inset-0 z-20 flex flex-col items-center justify-center cursor-pointer group/cover"
                @click="playThis(index)"
              >
                <img 
                  :src="item.cover" 
                  :alt="item.name" 
                  class="absolute inset-0 w-full h-full object-cover opacity-60 group-hover/cover:scale-105 transition-transform duration-700"
                />
                <div class="absolute inset-0 bg-black/40 group-hover/cover:bg-black/20 transition-colors"></div>
                
                <p class="relative z-30 text-white font-bold text-xl mb-4 drop-shadow-md">
                  {{ item.name }}
                </p>

                <div class="relative z-30 w-16 h-16 bg-primary text-black rounded-full flex items-center justify-center shadow-[0_0_20px_var(--color-primary)] group-hover/cover:scale-110 transition-transform">
                  <svg xmlns="http://www.w3.org/2000/svg" width="28" height="28" viewBox="0 0 24 24" fill="currentColor" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" class="ml-1"><polygon points="5 3 19 12 5 21 5 3"></polygon></svg>
                </div>
              </div>

              <iframe 
                v-if="playingIndex === index"
                style="border-radius:12px" 
                :src="`https://www.youtube.com/embed/videoseries?list=${item.id}&autoplay=1`" 
                width="100%" 
                height="100%" 
                frameBorder="0" 
                allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" 
                allowfullscreen 
                class="absolute inset-0 z-10">
              </iframe>

            </div>

          </div>
        </div>

      </div>

    </div>

    <div class="absolute bottom-0 w-full border-t border-white/5 pt-6 pb-6 text-center bg-darkbg/90 backdrop-blur-md z-20">
      <p class="text-gray-400 text-sm tracking-wide">
        Designed & Built by <span class="text-primary font-bold">Zakaria Fattawari</span>
      </p>
      <p class="text-gray-600 text-xs mt-2">
        © 2026 — All Rights Reserved.
      </p>
    </div>

  </section>
</template>

<script setup>
import { ref } from 'vue'

import coverImage1 from '../images/moodyblues.png' 
import coverImage2 from '../images/ger.png' 

const sendMessage = () => {
  alert("Message sent! I will get back to you soon.");
}

const myPlaylists = [
  {
    name: "Moody Blues",
    id: "PL51LO2h2cDWex4_SXzqILTqRcsOil-9lh",
    cover: coverImage1
  },
  {
    name: "Golden Experience - Requiem", 
    id: "PL51LO2h2cDWfteGHVk-W9_c-wQV8p-aDZ",
    cover: coverImage2
  }
]

const playingIndex = ref(null)

const playThis = (index) => {
  playingIndex.value = index;
}

const playlistSliderRef = ref(null)

const nextPlaylist = () => {
  if (playlistSliderRef.value) {
    const slider = playlistSliderRef.value
    if (slider.scrollLeft + slider.clientWidth >= slider.scrollWidth - 10) {
      slider.scrollTo({ left: 0, behavior: 'smooth' })
    } else {
      slider.scrollBy({ left: slider.clientWidth, behavior: 'smooth' })
    }
  }
}

const prevPlaylist = () => {
  if (playlistSliderRef.value) {
    const slider = playlistSliderRef.value
    if (slider.scrollLeft <= 10) {
      slider.scrollTo({ left: slider.scrollWidth, behavior: 'smooth' })
    } else {
      slider.scrollBy({ left: -slider.clientWidth, behavior: 'smooth' })
    }
  }
}
</script>

<style scoped>
.hide-scrollbar::-webkit-scrollbar {
  display: none;
}
.hide-scrollbar {
  -ms-overflow-style: none; 
  scrollbar-width: none; 
}
</style>