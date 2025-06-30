<template>
  <main class="products-page">
    <div class="container">
      <div class="page-header">
        <h1 class="page-title">📚 Semua Produk</h1>
        <p class="page-subtitle">Temukan buku favorit Anda dari koleksi lengkap kami</p>
      </div>
      
      <div class="filters-section">
        <div class="search-bar">
          <input 
            type="text" 
            v-model="searchQuery" 
            placeholder="Cari judul buku, penulis, atau genre..."
            class="search-input"
          >
          <button class="search-btn">🔍</button>
        </div>
        
        <div class="filter-controls">
          <select v-model="selectedGenre" class="filter-select">
            <option value="">Semua Genre</option>
            <option v-for="genre in genres" :key="genre" :value="genre">{{ genre }}</option>
          </select>
          
          <select v-model="sortBy" class="filter-select">
            <option value="title">Urutkan: Judul</option>
            <option value="price-low">Harga: Rendah ke Tinggi</option>
            <option value="price-high">Harga: Tinggi ke Rendah</option>
            <option value="rating">Rating Tertinggi</option>
          </select>
        </div>
      </div>
      
      <div class="products-section">
        <div class="results-info">
          <p>Menampilkan {{ filteredProducts.length }} dari {{ allProducts.length }} produk</p>
        </div>
        
        <div class="products-grid">
          <ProductCard 
            v-for="product in filteredProducts" 
            :key="product.id" 
            :product="product"
            @add-to-cart="handleAddToCart"
            @toggle-wishlist="handleToggleWishlist"
          />
        </div>
        
        <div v-if="filteredProducts.length === 0" class="no-results">
          <div class="no-results-icon">📚</div>
          <h3>Tidak ada produk ditemukan</h3>
          <p>Coba ubah kata kunci pencarian atau filter yang dipilih</p>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
import ProductCard from '../components/ProductCard.vue'

export default {
  name: 'Products',
  components: {
    ProductCard
  },
  data() {
    return {
      searchQuery: '',
      selectedGenre: '',
      sortBy: 'title',
      allProducts: [
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
        },
        {
          id: 7,
          title: 'Thinking, Fast and Slow',
          author: 'Daniel Kahneman',
          genre: 'Psychology',
          price: 110000,
          originalPrice: 145000,
          rating: 5,
          emoji: '🧠'
        },
        {
          id: 8,
          title: 'The Lean Startup',
          author: 'Eric Ries',
          genre: 'Business',
          price: 85000,
          originalPrice: 115000,
          rating: 4,
          emoji: '🚀'
        },
        {
          id: 9,
          title: 'Bumi Manusia',
          author: 'Pramoedya Ananta Toer',
          genre: 'Novel',
          price: 68000,
          originalPrice: 89000,
          rating: 5,
          emoji: '📖'
        },
        {
          id: 10,
          title: 'You Don\'t Know JS',
          author: 'Kyle Simpson',
          genre: 'Programming',
          price: 95000,
          originalPrice: 125000,
          rating: 4,
          emoji: '💻'
        },
        {
          id: 11,
          title: 'Rich Dad Poor Dad',
          author: 'Robert Kiyosaki',
          genre: 'Finance',
          price: 78000,
          originalPrice: 105000,
          rating: 4,
          emoji: '💰'
        },
        {
          id: 12,
          title: 'The 7 Habits of Highly Effective People',
          author: 'Stephen Covey',
          genre: 'Self Improvement',
          price: 92000,
          originalPrice: 125000,
          rating: 5,
          emoji: '📚'
        }
      ]
    }
  },
  computed: {
    genres() {
      return [...new Set(this.allProducts.map(product => product.genre))].sort()
    },
    filteredProducts() {
      let filtered = this.allProducts

      // Filter by search query
      if (this.searchQuery) {
        const query = this.searchQuery.toLowerCase()
        filtered = filtered.filter(product => 
          product.title.toLowerCase().includes(query) ||
          product.author.toLowerCase().includes(query) ||
          product.genre.toLowerCase().includes(query)
        )
      }

      // Filter by genre
      if (this.selectedGenre) {
        filtered = filtered.filter(product => product.genre === this.selectedGenre)
      }

      // Sort products
      filtered = [...filtered].sort((a, b) => {
        switch (this.sortBy) {
          case 'title':
            return a.title.localeCompare(b.title)
          case 'price-low':
            return a.price - b.price
          case 'price-high':
            return b.price - a.price
          case 'rating':
            return b.rating - a.rating
          default:
            return 0
        }
      })

      return filtered
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
.products-page {
  min-height: 100vh;
  background: #f8f9fa;
  padding: 2rem 0;
}

.container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 2rem;
}

.page-header {
  text-align: center;
  margin-bottom: 3rem;
}

.page-title {
  font-size: 2.5rem;
  color: #333;
  margin-bottom: 1rem;
  font-weight: bold;
}

.page-subtitle {
  font-size: 1.1rem;
  color: #666;
  max-width: 600px;
  margin: 0 auto;
}

.filters-section {
  background: white;
  padding: 2rem;
  border-radius: 16px;
  box-shadow: 0 4px 20px rgba(0,0,0,0.08);
  margin-bottom: 2rem;
}

.search-bar {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 1.5rem;
}

.search-input {
  flex: 1;
  padding: 1rem;
  border: 2px solid #e9ecef;
  border-radius: 12px;
  font-size: 1rem;
  transition: border-color 0.3s ease;
}

.search-input:focus {
  outline: none;
  border-color: #667eea;
}

.search-btn {
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border: none;
  padding: 1rem 1.5rem;
  border-radius: 12px;
  font-size: 1.2rem;
  cursor: pointer;
  transition: all 0.3s ease;
}

.search-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 15px rgba(102, 126, 234, 0.3);
}

.filter-controls {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}

.filter-select {
  padding: 0.8rem 1rem;
  border: 2px solid #e9ecef;
  border-radius: 8px;
  background: white;
  font-size: 0.9rem;
  cursor: pointer;
  transition: border-color 0.3s ease;
}

.filter-select:focus {
  outline: none;
  border-color: #667eea;
}

.products-section {
  background: white;
  padding: 2rem;
  border-radius: 16px;
  box-shadow: 0 4px 20px rgba(0,0,0,0.08);
}

.results-info {
  margin-bottom: 2rem;
  color: #666;
  font-size: 0.9rem;
}

.products-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(300px, 1fr));
  gap: 2rem;
}

.no-results {
  text-align: center;
  padding: 4rem 2rem;
  color: #666;
}

.no-results-icon {
  font-size: 4rem;
  margin-bottom: 1rem;
  opacity: 0.5;
}

.no-results h3 {
  font-size: 1.5rem;
  margin-bottom: 1rem;
  color: #333;
}

.no-results p {
  font-size: 1rem;
  max-width: 400px;
  margin: 0 auto;
}

@media screen and (max-width: 768px) {
  .page-title {
    font-size: 2rem;
  }
  
  .filters-section {
    padding: 1.5rem;
  }
  
  .filter-controls {
    flex-direction: column;
  }
  
  .filter-select {
    width: 100%;
  }
  
  .products-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }
  
  .products-section {
    padding: 1.5rem;
  }
  
  .container {
    padding: 0 1rem;
  }
}
</style>