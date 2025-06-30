<template>
  <div class="product-card">
    <div class="card-image">
      <div class="book-cover">{{ product.emoji }}</div>
      <div class="card-overlay">
        <button class="quick-view-btn">Lihat Detail</button>
      </div>
    </div>
    
    <div class="card-content">
      <h3 class="product-title">{{ product.title }}</h3>
      <p class="product-author">{{ product.author }}</p>
      <p class="product-genre">{{ product.genre }}</p>
      
      <div class="product-rating">
        <span class="stars">
          <span v-for="i in 5" :key="i" class="star" :class="{ filled: i <= product.rating }">★</span>
        </span>
        <span class="rating-text">({{ product.rating }}/5)</span>
      </div>
      
      <div class="product-price">
        <span class="current-price">Rp {{ formatPrice(product.price) }}</span>
        <span v-if="product.originalPrice" class="original-price">Rp {{ formatPrice(product.originalPrice) }}</span>
      </div>
      
      <div class="card-actions">
        <button class="add-to-cart-btn" @click="addToCart">
          <span class="cart-icon">🛒</span>
          Tambah ke Keranjang
        </button>
        <button class="wishlist-btn" @click="toggleWishlist" :class="{ active: isWishlisted }">
          <span class="heart-icon">{{ isWishlisted ? '❤️' : '🤍' }}</span>
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ProductCard',
  props: {
    product: {
      type: Object,
      required: true
    }
  },
  data() {
    return {
      isWishlisted: false
    }
  },
  methods: {
    formatPrice(price) {
      return price.toString().replace(/\B(?=(\d{3})+(?!\d))/g, '.')
    },
    addToCart() {
      // Implementasi add to cart
      console.log('Added to cart:', this.product.title)
      // Bisa emit event ke parent component
      this.$emit('add-to-cart', this.product)
    },
    toggleWishlist() {
      this.isWishlisted = !this.isWishlisted
      console.log('Wishlist toggled:', this.product.title)
      // Bisa emit event ke parent component
      this.$emit('toggle-wishlist', this.product)
    }
  }
}
</script>

<style scoped>
.product-card {
  background: white;
  border-radius: 16px;
  box-shadow: 0 4px 20px rgba(0,0,0,0.1);
  overflow: hidden;
  transition: all 0.3s ease;
  height: 100%;
  display: flex;
  flex-direction: column;
}

.product-card:hover {
  transform: translateY(-8px);
  box-shadow: 0 12px 40px rgba(0,0,0,0.15);
}

.card-image {
  position: relative;
  height: 200px;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  overflow: hidden;
}

.book-cover {
  font-size: 4rem;
  animation: float 3s ease-in-out infinite;
}

.card-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0,0,0,0.7);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.product-card:hover .card-overlay {
  opacity: 1;
}

.quick-view-btn {
  background: white;
  color: #333;
  border: none;
  padding: 0.8rem 1.5rem;
  border-radius: 25px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
}

.quick-view-btn:hover {
  transform: scale(1.05);
  box-shadow: 0 4px 15px rgba(0,0,0,0.2);
}

.card-content {
  padding: 1.5rem;
  flex: 1;
  display: flex;
  flex-direction: column;
}

.product-title {
  font-size: 1.2rem;
  font-weight: bold;
  color: #333;
  margin-bottom: 0.5rem;
  line-height: 1.3;
}

.product-author {
  color: #666;
  font-size: 0.9rem;
  margin-bottom: 0.3rem;
}

.product-genre {
  color: #888;
  font-size: 0.8rem;
  margin-bottom: 1rem;
  text-transform: uppercase;
  letter-spacing: 0.5px;
}

.product-rating {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

.stars {
  display: flex;
  gap: 2px;
}

.star {
  color: #ddd;
  font-size: 1rem;
  transition: color 0.2s ease;
}

.star.filled {
  color: #ffd700;
}

.rating-text {
  font-size: 0.8rem;
  color: #666;
}

.product-price {
  margin-bottom: 1.5rem;
}

.current-price {
  font-size: 1.3rem;
  font-weight: bold;
  color: #e74c3c;
}

.original-price {
  font-size: 0.9rem;
  color: #999;
  text-decoration: line-through;
  margin-left: 0.5rem;
}

.card-actions {
  display: flex;
  gap: 0.5rem;
  margin-top: auto;
}

.add-to-cart-btn {
  flex: 1;
  background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
  color: white;
  border: none;
  padding: 0.8rem 1rem;
  border-radius: 8px;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 0.5rem;
}

.add-to-cart-btn:hover {
  transform: translateY(-2px);
  box-shadow: 0 4px 15px rgba(102, 126, 234, 0.3);
}

.wishlist-btn {
  background: #f8f9fa;
  border: 2px solid #e9ecef;
  border-radius: 8px;
  padding: 0.8rem;
  cursor: pointer;
  transition: all 0.3s ease;
  display: flex;
  align-items: center;
  justify-content: center;
}

.wishlist-btn:hover {
  background: #e9ecef;
  transform: scale(1.05);
}

.wishlist-btn.active {
  background: #ffe6e6;
  border-color: #ff6b6b;
}

.heart-icon {
  font-size: 1.2rem;
}

@keyframes float {
  0%, 100% {
    transform: translateY(0px);
  }
  50% {
    transform: translateY(-10px);
  }
}

@media screen and (max-width: 768px) {
  .product-card {
    margin-bottom: 1rem;
  }
  
  .card-content {
    padding: 1rem;
  }
  
  .product-title {
    font-size: 1.1rem;
  }
  
  .add-to-cart-btn {
    padding: 0.7rem;
    font-size: 0.9rem;
  }
}
</style>