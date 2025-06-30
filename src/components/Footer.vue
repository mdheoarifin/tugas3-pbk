<template>
  <footer class="footer">
    <div class="footer-content">
      <div class="footer-section">
        <h3 class="footer-title">📚 Accell Store</h3>
        <p class="footer-description">
          Toko buku online terpercaya dengan koleksi lengkap dari berbagai genre. 
          Temukan buku favorit Anda dengan harga terjangkau dan layanan terbaik.
        </p>
        <div class="social-links">
          <a href="#" class="social-link">📘</a>
          <a href="#" class="social-link">📷</a>
          <a href="#" class="social-link">🐦</a>
          <a href="#" class="social-link">📺</a>
        </div>
      </div>
      
      <div class="footer-section">
        <h4 class="section-title">Kategori</h4>
        <ul class="footer-links">
          <li><a href="#">Novel</a></li>
          <li><a href="#">Pendidikan</a></li>
          <li><a href="#">Bisnis</a></li>
          <li><a href="#">Teknologi</a></li>
          <li><a href="#">Anak-anak</a></li>
        </ul>
      </div>
      
      <div class="footer-section">
        <h4 class="section-title">Layanan</h4>
        <ul class="footer-links">
          <li><a href="#">Pengiriman</a></li>
          <li><a href="#">Pengembalian</a></li>
          <li><a href="#">Bantuan</a></li>
          <li><a href="#">FAQ</a></li>
          <li><a href="#">Kontak</a></li>
        </ul>
      </div>
      
      <div class="footer-section">
        <h4 class="section-title">Informasi</h4>
        <ul class="footer-links">
          <li><a href="#">Tentang Kami</a></li>
          <li><a href="#">Kebijakan Privasi</a></li>
          <li><a href="#">Syarat & Ketentuan</a></li>
          <li><a href="#">Karir</a></li>
          <li><a href="#">Blog</a></li>
        </ul>
      </div>
      
      <div class="footer-section">
        <h4 class="section-title">Newsletter</h4>
        <p class="newsletter-text">Dapatkan update terbaru tentang buku dan penawaran khusus</p>
        <div class="newsletter-form">
          <input 
            type="email" 
            placeholder="Masukkan email Anda" 
            v-model="email"
            class="newsletter-input"
          >
          <button @click="subscribe" class="newsletter-btn">Berlangganan</button>
        </div>
      </div>
    </div>
    
    <div class="footer-bottom">
      <div class="footer-bottom-content">
        <p>&copy; 2025 BookStore. Semua hak dilindungi.</p>
        <div class="payment-methods">
          <span class="payment-text">Metode Pembayaran:</span>
          <div class="payment-icons">
            <span class="payment-icon">💳</span>
            <span class="payment-icon">🏦</span>
            <span class="payment-icon">📱</span>
            <span class="payment-icon">💰</span>
          </div>
        </div>
      </div>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'FooterSection',
  data() {
    return {
      email: ''
    }
  },
  methods: {
    subscribe() {
      if (this.email) {
        alert(`Terima kasih! Anda telah berlangganan dengan email: ${this.email}`)
        this.email = ''
      } else {
        alert('Mohon masukkan email yang valid')
      }
    }
  }
}
</script>

<style scoped>
.footer {
  background: linear-gradient(135deg, #2c3e50 0%, #34495e 100%);
  color: white;
  padding: 3rem 0 1rem;
  margin-top: 2rem;
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.footer-section {
  margin-bottom: 2rem;
}

.footer-title {
  font-size: 1.8rem;
  margin-bottom: 1rem;
  color: #3498db;
}

.footer-description {
  line-height: 1.6;
  color: #bdc3c7;
  margin-bottom: 1.5rem;
}

.social-links {
  display: flex;
  gap: 1rem;
}

.social-link {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  width: 40px;
  height: 40px;
  background: rgba(255,255,255,0.1);
  border-radius: 50%;
  text-decoration: none;
  font-size: 1.2rem;
  transition: all 0.3s ease;
}

.social-link:hover {
  background: #3498db;
  transform: translateY(-3px);
}

.section-title {
  font-size: 1.2rem;
  margin-bottom: 1rem;
  color: #3498db;
}

.footer-links {
  list-style: none;
  padding: 0;
}

.footer-links li {
  margin-bottom: 0.5rem;
}

.footer-links a {
  color: #bdc3c7;
  text-decoration: none;
  transition: color 0.3s ease;
}

.footer-links a:hover {
  color: #3498db;
}

.newsletter-text {
  color: #bdc3c7;
  margin-bottom: 1rem;
  line-height: 1.5;
}

.newsletter-form {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.newsletter-input {
  padding: 0.8rem;
  border: 1px solid #34495e;
  border-radius: 8px;
  background: rgba(255,255,255,0.1);
  color: white;
  font-size: 0.9rem;
}

.newsletter-input::placeholder {
  color: #bdc3c7;
}

.newsletter-input:focus {
  outline: none;
  border-color: #3498db;
  background: rgba(255,255,255,0.15);
}

.newsletter-btn {
  background: linear-gradient(135deg, #3498db 0%, #2980b9 100%);
  color: white;
  border: none;
  padding: 0.8rem 1.5rem;
  border-radius: 8px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
}

.newsletter-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 15px rgba(52, 152, 219, 0.3);
}

.footer-bottom {
  border-top: 1px solid #34495e;
  margin-top: 2rem;
  padding-top: 1.5rem;
}

.footer-bottom-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
  flex-wrap: wrap;
  gap: 1rem;
}

.payment-methods {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.payment-text {
  color: #bdc3c7;
  font-size: 0.9rem;
}

.payment-icons {
  display: flex;
  gap: 0.5rem;
}

.payment-icon {
  font-size: 1.5rem;
  opacity: 0.7;
  transition: opacity 0.3s ease;
}

.payment-icon:hover {
  opacity: 1;
}

@media screen and (max-width: 768px) {
  .footer-content {
    grid-template-columns: 1fr;
    text-align: center;
  }
  
  .footer-bottom-content {
    flex-direction: column;
    text-align: center;
  }
  
  .newsletter-form {
    max-width: 300px;
    margin: 0 auto;
  }
  
  .social-links {
    justify-content: center;
  }
}
</style>