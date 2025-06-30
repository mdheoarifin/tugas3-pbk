<template>
  <div class="carousel">
    <div class="carousel-container">
      <div 
        class="carousel-slide" 
        v-for="(slide, index) in slides" 
        :key="index"
        :class="{ active: currentSlide === index }"
      >
        <div class="slide-content">
          <div class="slide-text">
            <h1>{{ slide.title }}</h1>
            <p>{{ slide.subtitle }}</p>
            <button class="cta-button">{{ slide.buttonText }}</button>
          </div>
          <div class="slide-image">
            <div class="book-stack">📚</div>
          </div>
        </div>
      </div>
      
      <button class="carousel-btn prev" @click="prevSlide">‹</button>
      <button class="carousel-btn next" @click="nextSlide">›</button>
      
      <div class="carousel-indicators">
        <span 
          v-for="(slide, index) in slides" 
          :key="index"
          class="indicator"
          :class="{ active: currentSlide === index }"
          @click="goToSlide(index)"
        ></span>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Carousel',
  data() {
    return {
      currentSlide: 0,
      slides: [
        {
          title: 'Koleksi Buku Terlengkap',
          subtitle: 'Temukan ribuan buku dari berbagai genre dan penulis favorit Anda',
          buttonText: 'Jelajahi Sekarang'
        },
        {
          title: 'Harga Terjangkau',
          subtitle: 'Dapatkan buku berkualitas dengan harga yang ramah di kantong',
          buttonText: 'Lihat Penawaran'
        },
        {
          title: 'Pengiriman Cepat',
          subtitle: 'Buku pesanan Anda akan sampai dalam waktu 1-3 hari kerja',
          buttonText: 'Pesan Sekarang'
        }
      ]
    }
  },
  mounted() {
    this.startAutoSlide()
  },
  methods: {
    nextSlide() {
      this.currentSlide = (this.currentSlide + 1) % this.slides.length
    },
    prevSlide() {
      this.currentSlide = this.currentSlide === 0 ? this.slides.length - 1 : this.currentSlide - 1
    },
    goToSlide(index) {
      this.currentSlide = index
    },
    startAutoSlide() {
      setInterval(() => {
        this.nextSlide()
      }, 5000)
    }
  }
}
</script>

<style scoped>
.carousel {
  position: relative;
  height: 500px;
  overflow: hidden;
  background: linear-gradient(135deg, #f093fb 0%, #f5576c 100%);
}

.carousel-container {
  position: relative;
  height: 100%;
  width: 100%;
}

.carousel-slide {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  opacity: 0;
  transition: opacity 0.5s ease-in-out;
  display: flex;
  align-items: center;
  justify-content: center;
}

.carousel-slide.active {
  opacity: 1;
}

.slide-content {
  display: flex;
  align-items: center;
  justify-content: space-between;
  width: 100%;
  max-width: 1200px;
  padding: 0 2rem;
  color: white;
}

.slide-text {
  flex: 1;
  animation: slideInLeft 0.8s ease-out;
}

.slide-text h1 {
  font-size: 3rem;
  margin-bottom: 1rem;
  font-weight: bold;
}

.slide-text p {
  font-size: 1.2rem;
  margin-bottom: 2rem;
  opacity: 0.9;
}

.cta-button {
  background: rgba(255,255,255,0.2);
  color: white;
  border: 2px solid white;
  padding: 1rem 2rem;
  font-size: 1.1rem;
  border-radius: 50px;
  cursor: pointer;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
}

.cta-button:hover {
  background: white;
  color: #f5576c;
  transform: translateY(-3px);
  box-shadow: 0 10px 20px rgba(0,0,0,0.2);
}

.slide-image {
  flex: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

.book-stack {
  font-size: 8rem;
  animation: float 3s ease-in-out infinite;
}

.carousel-btn {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background: rgba(255,255,255,0.3);
  color: white;
  border: none;
  font-size: 2rem;
  padding: 1rem;
  cursor: pointer;
  border-radius: 50%;
  transition: all 0.3s ease;
  backdrop-filter: blur(10px);
}

.carousel-btn:hover {
  background: rgba(255,255,255,0.5);
  transform: translateY(-50%) scale(1.1);
}

.prev {
  left: 2rem;
}

.next {
  right: 2rem;
}

.carousel-indicators {
  position: absolute;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%);
  display: flex;
  gap: 1rem;
}

.indicator {
  width: 12px;
  height: 12px;
  border-radius: 50%;
  background: rgba(255,255,255,0.5);
  cursor: pointer;
  transition: all 0.3s ease;
}

.indicator.active {
  background: white;
  transform: scale(1.2);
}

@keyframes slideInLeft {
  from {
    opacity: 0;
    transform: translateX(-50px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes float {
  0%, 100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-20px);
  }
}

@media screen and (max-width: 768px) {
  .slide-content {
    flex-direction: column;
    text-align: center;
    padding: 1rem;
  }

  .slide-text h1 {
    font-size: 2rem;
  }

  .slide-text p {
    font-size: 1rem;
  }

  .book-stack {
    font-size: 4rem;
  }

  .carousel-btn {
    font-size: 1.5rem;
    padding: 0.5rem;
  }

  .prev {
    left: 1rem;
  }

  .next {
    right: 1rem;
  }
}
</style>