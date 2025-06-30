<template>
  <div class="about-page">
    <!-- Hero Section -->
    <section class="hero-section">
      <div class="hero-content">
        <div class="hero-text">
          <h1 class="hero-title">Tentang BookStore</h1>
          <p class="hero-subtitle">
            Destinasi terpercaya untuk semua kebutuhan literasi Anda sejak 2015
          </p>
        </div>
        <div class="hero-image">
          <div class="book-stack">
            <div class="book book-1"></div>
            <div class="book book-2"></div>
            <div class="book book-3"></div>
          </div>
        </div>
      </div>
    </section>

    <!-- Story Section -->
    <section class="story-section">
      <div class="container">
        <div class="story-content">
          <div class="story-text">
            <h2>Cerita Kami</h2>
            <p>
              BookStore lahir dari kecintaan mendalam terhadap dunia literasi. Dimulai dari sebuah 
              toko kecil di sudut kota, kami telah berkembang menjadi platform digital terdepan 
              yang melayani jutaan pembaca di seluruh Indonesia.
            </p>
            <p>
              Dengan koleksi lebih dari 100,000 judul buku dari berbagai genre dan penerbit 
              terkemuka, kami berkomitmen untuk menjadi jembatan antara penulis dan pembaca, 
              antara pengetahuan dan pencari ilmu.
            </p>
          </div>
          <div class="story-stats">
            <div class="stat-item">
              <div class="stat-number">{{ animatedStats.books }}</div>
              <div class="stat-label">Judul Buku</div>
            </div>
            <div class="stat-item">
              <div class="stat-number">{{ animatedStats.customers }}</div>
              <div class="stat-label">Pelanggan</div>
            </div>
            <div class="stat-item">
              <div class="stat-number">{{ animatedStats.years }}</div>
              <div class="stat-label">Tahun Pengalaman</div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- Mission Vision Section -->
    <section class="mission-section">
      <div class="container">
        <div class="mission-grid">
          <div class="mission-card">
            <div class="mission-icon">🎯</div>
            <h3>Misi Kami</h3>
            <p>
              Menyediakan akses mudah dan terjangkau ke dunia literasi untuk semua kalangan, 
              mendorong budaya membaca, dan mendukung perkembangan intelektual masyarakat Indonesia.
            </p>
          </div>
          <div class="mission-card">
            <div class="mission-icon">👁️</div>
            <h3>Visi Kami</h3>
            <p>
              Menjadi platform literasi digital terdepan di Asia Tenggara yang menginspirasi 
              jutaan orang untuk terus belajar dan berkembang melalui kekuatan buku.
            </p>
          </div>
        </div>
      </div>
    </section>

    <!-- Values Section -->
    <section class="values-section">
      <div class="container">
        <h2 class="section-title">Nilai-Nilai Kami</h2>
        <div class="values-grid">
          <div class="value-card" v-for="value in values" :key="value.id">
            <div class="value-icon">{{ value.icon }}</div>
            <h4>{{ value.title }}</h4>
            <p>{{ value.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Team Section -->
    <section class="team-section">
      <div class="container">
        <h2 class="section-title">Tim Kami</h2>
        <div class="team-grid">
          <div class="team-card" v-for="member in team" :key="member.id">
            <div class="team-avatar">
              <div class="avatar-placeholder">{{ member.initials }}</div>
            </div>
            <h4>{{ member.name }}</h4>
            <p class="team-role">{{ member.role }}</p>
            <p class="team-bio">{{ member.bio }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- Contact Info Section -->
    <section class="contact-section">
      <div class="container">
        <div class="contact-content">
          <div class="contact-info">
            <h2>Hubungi Kami</h2>
            <div class="contact-item">
              <div class="contact-icon">📍</div>
              <div>
                <strong>Alamat</strong>
                <p>Jl. Literasi No. 123, Jakarta Pusat 10110</p>
              </div>
            </div>
            <div class="contact-item">
              <div class="contact-icon">📞</div>
              <div>
                <strong>Telepon</strong>
                <p>+62 21 1234 5678</p>
              </div>
            </div>
            <div class="contact-item">
              <div class="contact-icon">✉️</div>
              <div>
                <strong>Email</strong>
                <p>info@bookstore.co.id</p>
              </div>
            </div>
          </div>
          <div class="contact-form">
            <h3>Kirim Pesan</h3>
            <form @submit.prevent="submitMessage">
              <div class="form-group">
                <input v-model="contactForm.name" type="text" placeholder="Nama Lengkap" required>
              </div>
              <div class="form-group">
                <input v-model="contactForm.email" type="email" placeholder="Email" required>
              </div>
              <div class="form-group">
                <textarea v-model="contactForm.message" placeholder="Pesan Anda" rows="5" required></textarea>
              </div>
              <button type="submit" class="submit-btn" :disabled="isSubmitting">
                {{ isSubmitting ? 'Mengirim...' : 'Kirim Pesan' }}
              </button>
            </form>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import { ref, onMounted, reactive } from 'vue'

export default {
  name: 'About',
  setup() {
    const animatedStats = reactive({
      books: 0,
      customers: 0,
      years: 0
    })

    const contactForm = reactive({
      name: '',
      email: '',
      message: ''
    })

    const isSubmitting = ref(false)

    const values = ref([
      {
        id: 1,
        icon: '💎',
        title: 'Kualitas',
        description: 'Kami berkomitmen menyediakan buku-buku berkualitas tinggi dari penerbit terpercaya.'
      },
      {
        id: 2,
        icon: '🚀',
        title: 'Inovasi',
        description: 'Terus berinovasi dalam teknologi dan layanan untuk pengalaman belanja yang lebih baik.'
      },
      {
        id: 3,
        icon: '🤝',
        title: 'Kepercayaan',
        description: 'Membangun kepercayaan melalui pelayanan yang jujur, transparan, dan dapat diandalkan.'
      },
      {
        id: 4,
        icon: '🌟',
        title: 'Kepuasan',
        description: 'Mengutamakan kepuasan pelanggan dengan layanan terbaik dan pengalaman yang menyenangkan.'
      }
    ])

    const team = ref([
      {
        id: 1,
        name: 'Andi Pratama',
        initials: 'AP',
        role: 'CEO & Founder',
        bio: 'Pecinta buku dengan visi memajukan literasi Indonesia melalui teknologi.'
      },
      {
        id: 2,
        name: 'Sari Dewi',
        initials: 'SD',
        role: 'Head of Operations',
        bio: 'Ahli dalam manajemen operasional dengan pengalaman 10+ tahun di industri retail.'
      },
      {
        id: 3,
        name: 'Budi Santoso',
        initials: 'BS',
        role: 'CTO',
        bio: 'Developer berpengalaman yang passionate dalam menciptakan solusi teknologi inovatif.'
      },
      {
        id: 4,
        name: 'Maya Kusuma',
        initials: 'MK',
        role: 'Head of Marketing',
        bio: 'Kreator konten dan strategis marketing dengan keahlian dalam digital marketing.'
      }
    ])

    const animateNumbers = () => {
      const targets = { books: 100000, customers: 50000, years: 9 }
      const duration = 2000
      const steps = 60

      Object.keys(targets).forEach(key => {
        const target = targets[key]
        const increment = target / steps
        let current = 0
        
        const timer = setInterval(() => {
          current += increment
          if (current >= target) {
            animatedStats[key] = target.toLocaleString()
            clearInterval(timer)
          } else {
            animatedStats[key] = Math.floor(current).toLocaleString()
          }
        }, duration / steps)
      })
    }

    const submitMessage = async () => {
      isSubmitting.value = true
      
      // Simulasi pengiriman pesan
      await new Promise(resolve => setTimeout(resolve, 1500))
      
      alert('Pesan Anda telah terkirim! Kami akan segera menghubungi Anda.')
      
      // Reset form
      contactForm.name = ''
      contactForm.email = ''
      contactForm.message = ''
      
      isSubmitting.value = false
    }

    onMounted(() => {
      // Start number animation after component is mounted
      setTimeout(animateNumbers, 500)
    })

    return {
      animatedStats,
      contactForm,
      isSubmitting,
      values,
      team,
      submitMessage
    }
  }
}
</script>

<style scoped>
.about-page {
  min-height: 100vh;
}

/* Hero Section */
.hero-section {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  padding: 80px 20px;
  overflow: hidden;
}

.hero-content {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
  align-items: center;
}

.hero-title {
  font-size: 3.5rem;
  font-weight: 700;
  margin-bottom: 20px;
  line-height: 1.2;
}

.hero-subtitle {
  font-size: 1.3rem;
  opacity: 0.9;
  line-height: 1.6;
}

.hero-image {
  display: flex;
  justify-content: center;
  align-items: center;
}

.book-stack {
  position: relative;
  width: 200px;
  height: 250px;
}

.book {
  position: absolute;
  width: 120px;
  height: 160px;
  border-radius: 8px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.3);
}

.book-1 {
  background: #ff6b6b;
  top: 0;
  left: 0;
  transform: rotate(-10deg);
  z-index: 3;
}

.book-2 {
  background: #4ecdc4;
  top: 20px;
  left: 40px;
  transform: rotate(5deg);
  z-index: 2;
}

.book-3 {
  background: #45b7d1;
  top: 40px;
  left: 80px;
  transform: rotate(15deg);
  z-index: 1;
}

/* Container */
.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
}

/* Story Section */
.story-section {
  padding: 80px 0;
  background: #f8f9fa;
}

.story-content {
  display: grid;
  grid-template-columns: 2fr 1fr;
  gap: 60px;
  align-items: center;
}

.story-text h2 {
  font-size: 2.5rem;
  color: #2c3e50;
  margin-bottom: 30px;
}

.story-text p {
  font-size: 1.1rem;
  line-height: 1.8;
  color: #5a6c7d;
  margin-bottom: 20px;
}

.story-stats {
  display: flex;
  flex-direction: column;
  gap: 30px;
}

.stat-item {
  text-align: center;
  padding: 30px;
  background: white;
  border-radius: 12px;
  box-shadow: 0 5px 15px rgba(0,0,0,0.1);
}

.stat-number {
  font-size: 2.5rem;
  font-weight: 700;
  color: #667eea;
  margin-bottom: 10px;
}

.stat-label {
  font-size: 1rem;
  color: #5a6c7d;
  font-weight: 500;
}

/* Mission Section */
.mission-section {
  padding: 80px 0;
}

.mission-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(400px, 1fr));
  gap: 40px;
}

.mission-card {
  background: white;
  padding: 40px;
  border-radius: 16px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.1);
  text-align: center;
  transition: transform 0.3s ease;
}

.mission-card:hover {
  transform: translateY(-5px);
}

.mission-icon {
  font-size: 3rem;
  margin-bottom: 20px;
}

.mission-card h3 {
  font-size: 1.5rem;
  color: #2c3e50;
  margin-bottom: 20px;
}

.mission-card p {
  color: #5a6c7d;
  line-height: 1.7;
}

/* Values Section */
.values-section {
  padding: 80px 0;
  background: #f8f9fa;
}

.section-title {
  text-align: center;
  font-size: 2.5rem;
  color: #2c3e50;
  margin-bottom: 60px;
}

.values-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 30px;
}

.value-card {
  background: white;
  padding: 30px;
  border-radius: 12px;
  text-align: center;
  box-shadow: 0 5px 15px rgba(0,0,0,0.1);
  transition: transform 0.3s ease;
}

.value-card:hover {
  transform: translateY(-3px);
}

.value-icon {
  font-size: 2.5rem;
  margin-bottom: 20px;
}

.value-card h4 {
  font-size: 1.3rem;
  color: #2c3e50;
  margin-bottom: 15px;
}

.value-card p {
  color: #5a6c7d;
  line-height: 1.6;
}

/* Team Section */
.team-section {
  padding: 80px 0;
}

.team-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 40px;
}

.team-card {
  background: white;
  padding: 30px;
  border-radius: 16px;
  text-align: center;
  box-shadow: 0 10px 30px rgba(0,0,0,0.1);
  transition: transform 0.3s ease;
}

.team-card:hover {
  transform: translateY(-5px);
}

.team-avatar {
  margin-bottom: 20px;
}

.avatar-placeholder {
  width: 80px;
  height: 80px;
  border-radius: 50%;
  background: linear-gradient(135deg, #667eea, #764ba2);
  color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  font-size: 1.5rem;
  font-weight: 600;
  margin: 0 auto;
}

.team-card h4 {
  font-size: 1.3rem;
  color: #2c3e50;
  margin-bottom: 5px;
}

.team-role {
  color: #667eea;
  font-weight: 600;
  margin-bottom: 15px;
}

.team-bio {
  color: #5a6c7d;
  line-height: 1.6;
  font-size: 0.95rem;
}

/* Contact Section */
.contact-section {
  padding: 80px 0;
  background: #f8f9fa;
}

.contact-content {
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 60px;
}

.contact-info h2 {
  font-size: 2.5rem;
  color: #2c3e50;
  margin-bottom: 40px;
}

.contact-item {
  display: flex;
  align-items: flex-start;
  gap: 20px;
  margin-bottom: 30px;
}

.contact-icon {
  font-size: 1.5rem;
  margin-top: 5px;
}

.contact-item strong {
  color: #2c3e50;
  font-size: 1.1rem;
  display: block;
  margin-bottom: 5px;
}

.contact-item p {
  color: #5a6c7d;
  margin: 0;
}

.contact-form {
  background: white;
  padding: 40px;
  border-radius: 16px;
  box-shadow: 0 10px 30px rgba(0,0,0,0.1);
}

.contact-form h3 {
  font-size: 1.5rem;
  color: #2c3e50;
  margin-bottom: 30px;
}

.form-group {
  margin-bottom: 20px;
}

.form-group input,
.form-group textarea {
  width: 100%;
  padding: 15px;
  border: 2px solid #e1e8ed;
  border-radius: 8px;
  font-size: 1rem;
  transition: border-color 0.3s ease;
}

.form-group input:focus,
.form-group textarea:focus {
  outline: none;
  border-color: #667eea;
}

.submit-btn {
  width: 100%;
  padding: 15px;
  background: linear-gradient(135deg, #667eea, #764ba2);
  color: white;
  border: none;
  border-radius: 8px;
  font-size: 1.1rem;
  font-weight: 600;
  cursor: pointer;
  transition: opacity 0.3s ease;
}

.submit-btn:hover:not(:disabled) {
  opacity: 0.9;
}

.submit-btn:disabled {
  opacity: 0.6;
  cursor: not-allowed;
}

/* Responsive Design */
@media (max-width: 768px) {
  .hero-content,
  .story-content,
  .contact-content {
    grid-template-columns: 1fr;
    gap: 40px;
  }
  
  .hero-title {
    font-size: 2.5rem;
  }
  
  .mission-grid {
    grid-template-columns: 1fr;
  }
  
  .story-stats {
    flex-direction: row;
    justify-content: space-around;
  }
  
  .stat-item {
    padding: 20px;
  }
  
  .stat-number {
    font-size: 2rem;
  }
}

@media (max-width: 480px) {
  .hero-section {
    padding: 60px 20px;
  }
  
  .hero-title {
    font-size: 2rem;
  }
  
  .hero-subtitle {
    font-size: 1.1rem;
  }
  
  .story-stats {
    flex-direction: column;
    gap: 20px;
  }
  
  .section-title {
    font-size: 2rem;
  }
  
  .values-grid,
  .team-grid {
    grid-template-columns: 1fr;
  }
}
</style>