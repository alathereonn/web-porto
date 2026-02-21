<template>
  <section id="about" class="relative py-24 px-6 overflow-hidden">

    <!-- Nebula -->
    <div class="absolute inset-0 pointer-events-none z-0">
      <div class="nebula-layer layer1"></div>
      <div class="nebula-layer layer2"></div>
      <div class="nebula-layer layer3"></div>
    </div>

    <!-- ================= CAROUSEL ================= -->
    <div
      class="max-w-5xl mx-auto relative overflow-hidden cursor-grab z-10"
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
          class="flex-shrink-0"
          :style="{ width: slideWidth + 'px', padding: '0 49px' }"
        >
          <div class="relative w-full aspect-[4/3] py-5">
            <img
              :src="img"
              class="carousel-image"
            />
          </div>
        </div>
      </div>
    </div>

    <!-- ================= ABOUT CONTENT ================= -->
    <div class="max-w-7xl mx-auto mt-24 grid md:grid-cols-2 gap-16 relative z-10">

      <!-- LEFT -->
      <div class="text-gray-300 leading-relaxed space-y-6 text-justify">

      <h2 class="text-4xl md:text-5xl font-bold leading-tight">
        <span class="text-primary">
          {{ displayAbout }}
        </span>
        <span class="animate-pulse text-primary drop-shadow-[0_0_8px_var(--color-primary)]">
          |
        </span>
      </h2>

        <p>
          My name is <span class="text-primary font-bold">Zakaria Fattawari</span>,
          a third-year Computer Science student at <span class="text-primary font-bold">Kalimantan Institute of Technology</span>.
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

      <!-- RIGHT CARDS -->
      <div class="space-y-8">
        <div class="info-card">
          <h3 class="card-title">Education</h3>
          <p>
            Computer Science – Kalimantan Institute of Technology<br>
            Faculty of Science & Information Technology
          </p>
        </div>

        <div class="info-card">
          <h3 class="card-title">Interest / Skills</h3>
          <ul class="list-disc list-inside space-y-1">
            <li>Web Development</li>
            <li>Game Development</li>
            <li>Computer Networks</li>
            <li>Artificial Intelligence</li>
            <li>Machine Learning</li>
          </ul>
        </div>

        <div class="info-card">
          <h3 class="card-title">Philosophy</h3>
          <p class="italic text-400">
            "Even if the world ends and disappears, it will be just two of us, alone in the memory."
          </p>
        </div>
      </div>
    </div>

    <!-- MORE BUTTON -->
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
      aboutTexts: ["ABOUT ME", "WHO AM I", "GET TO KNOW ME", "WHAT DO I DO?"],
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
      this.slideWidth = container.offsetWidth;
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
        slider.style.transition = 'none';

        if (this.currentIndex === 0)
          this.currentIndex = this.images.length;

        if (this.currentIndex === this.images.length + 1)
          this.currentIndex = 1;

        slider.style.transform = `translateX(${-this.currentIndex * this.slideWidth}px)`;
        void slider.offsetWidth;
        slider.style.transition = 'transform 0.5s ease-in-out';
      }, 500);
    },

    scrollToQualification() {
      const section = document.getElementById('qualification');
      if (section) {
        section.scrollIntoView({ behavior: 'smooth' });
      }
    }
  }
};
</script>