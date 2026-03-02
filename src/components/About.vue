<template>
  <section id="about" class="relative min-h-screen flex flex-col justify-center items-center pt-20 pb-20 overflow-hidden w-full">
    
    <h2 class="text-4xl md:text-5xl font-bold text-center mb-12 md:mb-20">
      About <span class="text-primary">Me!</span>
    </h2>

    <div class="absolute inset-0 pointer-events-none z-0">
      <div class="nebula-layer layer1"></div>
      <div class="nebula-layer layer2"></div>
      <div class="nebula-layer layer3"></div>
    </div>

    <div
      class="w-full max-w-5xl mx-auto relative overflow-hidden cursor-grab z-10"
      @mousedown="onDragStart"
      @mousemove="onDragMove"
      @mouseup="onDragEnd"
      @mouseleave="onDragEnd"
      @touchstart="onDragStart"
      @touchmove="onDragMove"
      @touchend="onDragEnd"
    >
      <div
        ref="slider"
        class="flex transition-transform duration-500 ease-in-out"
        :style="sliderStyle"
      >
        <div
          v-for="(img, i) in loopImages"
          :key="i"
          class="flex-shrink-0 px-4 md:px-12"
          :style="{ width: slideWidth + 'px' }"
        >
          <div class="relative w-full aspect-[4/3] py-2 md:py-5">
            <img
              :src="img"
              class="carousel-image rounded-2xl shadow-lg object-cover w-full h-full"
            />
          </div>
        </div>
      </div>
    </div>

    <div class="w-full max-w-7xl mx-auto px-6 mt-12 md:mt-24 grid md:grid-cols-2 gap-10 md:gap-16 relative z-10">

      <div class="text-gray-300 leading-relaxed space-y-6 text-left md:text-justify">

      <h2 class="text-3xl md:text-5xl font-bold leading-tight">
        <span class="text-primary">
          {{ displayAbout }}
        </span>
        <span class="animate-pulse text-primary drop-shadow-[0_0_8px_var(--color-primary)]">
          |
        </span>
      </h2>

        <p>
          My name is Zakaria Fattawari, a third-year
          <a href="https://if.itk.ac.id/" target="_blank" rel="noopener noreferrer" 
             class="text-primary font-bold hover:text-white transition-colors underline decoration-primary/30 underline-offset-4"> 
          Computer Science 
          </a> student at 
          <a href="https://itk.ac.id" target="_blank" rel="noopener noreferrer" 
             class="text-primary font-bold hover:text-white transition-colors underline decoration-primary/30 underline-offset-4">
            Kalimantan Institute of Technology
          </a>.
          I have a strong interest in Web Development, Artificial Intelligence, and
          Machine Learning. I am currently deepening my knowledge in database systems 
          and full-stack development to strengthen my technical foundation and broaden my expertise.
        </p>

        <p>
          What I do is transform ideas into functional digital solutions.
          I design and develop responsive web applications, build backend systems,
          and explore intelligent systems using AI and Machine Learning.
          I enjoy working across the full development cycle from planning,
          designing system architecture, developing features, to testing.
        </p>

        <p>
          Despite starting without a technical background, I continuously challenge
          myself to grow and adapt in the field of Informatics. This journey has
          strengthened my problem-solving mindset, analytical thinking, and
          ability to learn independently. I am currently strengthening my foundation
          in databases, API development, and system architecture to become a
          well-rounded full-stack developer.
        </p>

        <p>
          Beyond technical development, I am also active as a facilitator or a Guider in
          Student Managerial Skills Training (LKMM), contributing to leadership
          and organizational development among students. Through this role,
          I develop communication, teamwork, and project coordination skills
          that complement my technical expertise.
        </p>
      </div>

      <div class="space-y-6 md:space-y-8">
        <div class="info-card bg-card p-6 rounded-2xl border border-white/5 shadow-xl">
          <h3 class="text-xl font-bold text-primary mb-3">Education</h3>
          <p class="text-gray-300 text-sm md:text-base space-y-2">
            <span class="block">> Undergraduate Computer Science Student</span>
            <span class="block">> Kalimantan Institute of Technology</span>
            <span class="block">> Faculty of Science & Information Technology</span>
          </p>
        </div>

        <div class="info-card bg-card p-6 rounded-2xl border border-white/5 shadow-xl">
          <h3 class="text-xl font-bold text-primary mb-3">Interest / Skills</h3>
          <ul class="list-disc list-inside space-y-1 text-gray-300 text-sm md:text-base">
            <li>Web Development</li>
            <li>Game Development</li>
            <li>Computer Networks</li>
            <li>Artificial Intelligence</li>
            <li>Machine Learning</li>
          </ul>
        </div>

        <div class="info-card bg-card p-6 rounded-2xl border border-white/5 shadow-xl">
          <p class="italic text-gray-400 text-sm md:text-base">
            "Even if the world ends and disappears, it will be just two of us, alone in the memory."
          </p>
        </div>
      </div>
    </div>

    <div class="flex justify-center mt-16 relative z-10">
      <button
        @click="scrollToQualification"
        class="group relative px-10 py-4 rounded-xl
              font-semibold tracking-wide
              border border-primary
              text-primary
              bg-transparent
              transition-all duration-300
              transform
              shadow-[0_6px_0_0_var(--color-primary)]
              
              hover:bg-primary
              hover:text-black
              hover:-translate-y-1
              hover:shadow-[0_12px_25px_var]

              active:translate-y-2
              active:shadow-[0_3px_0_0_var(--color-primary)]"
      >
        More
      </button>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      images: [
        'src/images/1.jpeg',
        'src/images/2.jpeg',
        'src/images/3.jpeg'
      ],

      currentIndex: 1,
      slideWidth: 0,
      isDragging: false,
      startX: 0,
      dragOffset: 0,
      autoSlideInterval: null,

      // ===== TYPING DATA =====
      aboutTexts: ["WHO AM I", "GET TO KNOW ME", "WHAT DO I DO?"],
      displayAbout: ""
    };
  },

  computed: {
    loopImages() {
      return [this.images[this.images.length - 1], ...this.images, this.images[0]];
    },
    sliderStyle() {
      return {
        transform: `translateX(${-this.currentIndex * this.slideWidth + this.dragOffset}px)`,
        transition: this.isDragging ? 'none' : 'transform 0.5s ease-in-out'
      };
    }
  },

  mounted() {
    this.updateSlideWidth();
    window.addEventListener('resize', this.updateSlideWidth);

    this.autoSlideInterval = setInterval(() => {
      this.slideTo(this.currentIndex + 1);
    }, 5000);

    // START TYPING
    this.createTypingEffect(this.aboutTexts, 120, 60, 1500);
  },

  beforeUnmount() {
    window.removeEventListener('resize', this.updateSlideWidth);
    clearInterval(this.autoSlideInterval);
  },

  methods: {

    // ===== TYPING EFFECT =====
    createTypingEffect(texts, typingSpeed, deletingSpeed, delay) {
      let textIndex = 0;
      let charIndex = 0;
      let isDeleting = false;

      const type = () => {
        const currentText = texts[textIndex];

        if (!isDeleting) {
          this.displayAbout = currentText.substring(0, charIndex++);
          if (charIndex > currentText.length) {
            setTimeout(() => isDeleting = true, delay);
          }
        } else {
          this.displayAbout = currentText.substring(0, charIndex--);
          if (charIndex < 0) {
            isDeleting = false;
            textIndex = (textIndex + 1) % texts.length;
          }
        }

        setTimeout(type, isDeleting ? deletingSpeed : typingSpeed);
      };

      type();
    },

    // ===== CAROUSEL METHODS =====
    updateSlideWidth() {
      const container = this.$el.querySelector('.overflow-hidden');
      if (container) {
        this.slideWidth = container.offsetWidth;
      }
    },

    getClientX(e) {
      return e.type.includes('mouse') ? e.clientX : e.touches[0].clientX;
    },

    onDragStart(e) {
      this.isDragging = true;
      this.startX = this.getClientX(e);
      clearInterval(this.autoSlideInterval);
    },

    onDragMove(e) {
      if (!this.isDragging) return;
      this.dragOffset = this.getClientX(e) - this.startX;
    },

    onDragEnd() {
      if (!this.isDragging) return;

      const threshold = 10;

      if (this.dragOffset < -threshold)
        this.slideTo(this.currentIndex + 1);
      else if (this.dragOffset > threshold)
        this.slideTo(this.currentIndex - 1);
      else
        this.slideTo(this.currentIndex);

      this.dragOffset = 0;
      this.isDragging = false;

      this.autoSlideInterval = setInterval(() => {
        this.slideTo(this.currentIndex + 1);
      }, 5000);
    },

    slideTo(index) {
      this.currentIndex = index;

      setTimeout(() => {
        const slider = this.$refs.slider;
        if (!slider) return;
        slider.style.transition = 'none';

        if (this.currentIndex === 0)
          this.currentIndex = this.images.length;

        if (this.currentIndex === this.images.length + 1)
          this.currentIndex = 1;

        slider.style.transform = `translateX(${-this.currentIndex * this.slideWidth}px)`;
        void slider.offsetWidth; // Trigger reflow
        slider.style.transition = 'transform 0.5s ease-in-out';
      }, 500);
    },

    scrollToQualification() {
      const target = document.getElementById('qualification');
      if (target) {
        const start = window.pageYOffset;
        const end = target.getBoundingClientRect().top + start - 100; 
        
        window.scrollTo({
          top: end,
          behavior: 'smooth'
        });
      }
    }
  }
};
</script>