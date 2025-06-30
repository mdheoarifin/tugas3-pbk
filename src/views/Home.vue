<template>
  <main class="home">
    <Carousel />
    
    <section class="featured-products">
      <div class="container">
        <div class="section-header">
          <h2 class="section-title">📖 Buku Pilihan</h2>
          <p class="section-subtitle">Koleksi buku terbaik yang dipilih khusus untuk Anda</p>
        </div>
        
        <div class="products-grid">
          <ProductCard 
            v-for="product in featuredProducts" 
            :key="product.id" 
            :product="product"
            @add-to-cart="handleAddToCart"
            @toggle-wishlist="handleToggleWishlist"
          />
        </div>
        
        <div class="section-footer">
          <router-link to="/products" class="view-all-btn">
            Lihat Semua Produk
            <span class="arrow">→</span>
          </router-link>
        </div>
      </div>
    </section>
    
    <section class="features">
      <div class="container">
        <div class="features-grid">
          <div class="feature-card">
            <div class="feature-icon">🚚</div>
            <h3>Pengiriman Gratis</h3>
            <p>Gratis ongkir untuk pembelian di atas Rp 150.000</p>
          </div>
          
          <div class="feature-card">
            <div class="feature-icon">🔒</div>
            <h3>Pembayaran Aman</h3>
            <p>Transaksi dijamin aman dengan berbagai metode pembayaran</p>
          </div>
          
          <div class="feature-card">
            <div class="feature-icon">⭐</div>
            <h3>Kualitas Terjamin</h3>
            <p>Semua buku original dan berkualitas tinggi</p>
          </div>
          
          <div class="feature-card">
            <div class="feature-icon">🎧</div>
            <h3>Customer Service 24/7</h3>
            <p>Tim support siap membantu Anda kapan saja</p>
          </div>
        </div>
      </div>
    </section>
  </main>
</template>

<script>
import Carousel from '../components/Carousel.vue'
import ProductCard from '../components/ProductCard.vue'

export default {
  name: 'Home',
  components: {
    Carousel,
    ProductCard
  },
  data() {
    return {
      featuredProducts: [
        {
          id: 1,
          title: 'Atomic Habits',
          author: 'James Clear',
          genre: 'Self Improvement',
          price: 89000,
          originalPrice: 120000,
          rating: 5,
          emoji: '📚'
        },
        {
          id: 2,
          title: 'Sapiens',
          author: 'Yuval Noah Harari',
          genre: 'History',
          price: 95000,
          originalPrice: 135000,
          rating: 5,
          emoji: '🧠'
        },
        {
          id: 3,
          title: 'The Psychology of Money',
          author: 'Morgan Housel',
          genre: 'Finance',
          price: 75000,
          originalPrice: 98000,
          rating: 4,
          emoji: '💰'
        },
        {
          id: 4,
          title: 'Clean Code',
          author: 'Robert C. Martin',
          genre: 'Programming',
          price: 125000,
          originalPrice: 165000,
          rating: 5,
          emoji: '💻'
        },
        {
          id: 5,
          title: 'Filosofi Teras',
          author: 'Henry Manampiring',
          genre: 'Philosophy',
          price: 65000,
          originalPrice: 85000,
          rating: 4,
          emoji: '🏛️'
        },
        {
          id: 6,
          title: 'Cantik Itu Luka',
          author: 'Eka Kurniawan',
          genre: 'Novel',
          price: 72000,
          originalPrice: 95000,
          rating: 4,
          emoji: '📖'
        }
      ]
    }
  },
  methods: {
    handleAddToCart(product) {
      console.log('Product added to cart:', product.title)
      // Implementasi logika add to cart
    },
    handleToggleWishlist(product) {
      console.log('Wishlist toggled for:', product.title)
      // Implementasi logika wishlist
    }
  }
}
</script>

<style scoped>
.home {
  min-height: 100vh;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.featured-products {
  padding: 4rem 0;
  background: #f8f9fa;
}

.section-header {
  text-align: center;
  margin-bottom: 3rem;
}

.section-title {
  font-size: 2.5rem;
  color: #333;
  margin-bottom: 1rem;
  font-weight: bold;
}

.section-subtitle {
  font-size: 1.1rem;
  color: #666;
  max-width: 600px;
  margin: 0 auto;
}

.products-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  gap: 2rem;
  margin-bottom: 3rem;
}

.section-footer {
  text-align: center;
}

.view-all-btn {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  text-decoration: none;
  padding: 1rem 2rem;
  border-radius: 50px;
  font-weight: 600;
  font-size: 1.1rem;
  transition: all 0.3s ease;
}

.view-all-btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 10px 25px rgba(102, 126, 234, 0.3);
}

.arrow {
  transition: transform 0.3s ease;
}

.view-all-btn:hover .arrow {
  transform: translateX(5px);
}

.features {
  padding: 4rem 0;
  background: white;
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.feature-card {
  text-align: center;
  padding: 2rem;
  border-radius: 16px;
  background: white;
  box-shadow: 0 4px 20px rgba(0,0,0,0.08);
  transition: all 0.3s ease;
}

.feature-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 30px rgba(0,0,0,0.12);
}

.feature-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
}

.feature-card h3 {
  font-size: 1.3rem;
  color: #333;
  margin-bottom: 1rem;
  font-weight: bold;
}

.feature-card p {
  color: #666;
  line-height: 1.6;
}

@media screen and (max-width: 768px) {
  .section-title {
    font-size: 2rem;
  }
  
  .products-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }
  
  .features-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }
  
  .feature-card {
    padding: 1.5rem;
  }
  
  .container {
    padding: 0 1rem;
  }
}
</style>