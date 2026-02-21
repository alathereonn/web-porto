<template>
  <section id="qualification" class="qualification-section">

    <h2 class="text-4xl md:text-5xl font-bold leading-tight text-center mb-24">
      <span class="text-primary">
        {{ typedText }}
      </span>
      <span class="animate-pulse text-primary drop-shadow-[0_0_8px_var(--color-primary)]">
        |
      </span>
    </h2>

    <div class="timeline">
      <div class="timeline-item left">
        <div class="timeline-content">
          <h3>MikroTik Certified Network Associate</h3>
          <p class="heldby">Held by Mikrotik and Kalimantan Institute of Technology</p>
          <p class="description">MikroTik Certified Network Associate (MTCNA) is the foundational, entry-level certification for MikroTik networking, focusing on basic configuration, troubleshooting, and management of RouterOS software and RouterBOARD hardware</p>
          <span class="date">
            <svg 
              xmlns="http://www.w3.org/2000/svg"
              class="calendar-icon"
              fill="none"
              viewBox="0 0 24 24"
              stroke="currentColor"
              stroke-width="1.8"
            >
              <path stroke-linecap="round" stroke-linejoin="round"
                d="M8 7V3m8 4V3m-9 8h10M5 21h14a2 2 0 002-2V7a2 2 0 00-2-2H5a2 2 0 00-2 2v12a2 2 0 002 2z" />
            </svg>

            May 19, 2025 - May 20, 2025
          </span>
        </div>
      </div>
    </div>

  </section>
</template>

<script>
export default {
  data() {
    return {
      texts: [
        "PROFESSIONAL CERTIFICATION"
      ],
      typedText: "",
      typingSpeed: 100,
      deletingSpeed: 50,
      delay: 1500
    };
  },

  mounted() {
    this.startTyping();
  },

  methods: {
    startTyping() {
      let textIndex = 0;
      let charIndex = 0;
      let isDeleting = false;

      const loop = () => {
        const current = this.texts[textIndex];

        if (!isDeleting) {
          this.typedText = current.substring(0, charIndex++);
          if (charIndex > current.length) {
            setTimeout(() => isDeleting = true, this.delay);
          }
        } else {
          this.typedText = current.substring(0, charIndex--);
          if (charIndex < 0) {
            isDeleting = false;
            textIndex = (textIndex + 1) % this.texts.length;
          }
        }

        setTimeout(loop, isDeleting ? this.deletingSpeed : this.typingSpeed);
      };

      loop();
    }
  }
};
</script>