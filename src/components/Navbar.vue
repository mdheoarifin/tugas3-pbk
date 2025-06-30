<template>
  <nav class="navbar">
    <div class="nav-container">
      <div class="nav-logo">
        <router-link to="/" class="nav-logo-link">
          <div class="logo-content">
            <span class="logo-icon">📚</span>
            <h2>Accell Store</h2>
          </div>
        </router-link>
      </div>
             
      <div class="nav-menu" :class="{ active: isOpen }">
        <router-link to="/" class="nav-link" @click="closeMenu">
          <span class="link-text">Beranda</span>
          <span class="link-underline"></span>
        </router-link>
        <router-link to="/products" class="nav-link" @click="closeMenu">
          <span class="link-text">Produk</span>
          <span class="link-underline"></span>
        </router-link>
        <router-link to="/about" class="nav-link" @click="closeMenu">
          <span class="link-text">Tentang</span>
          <span class="link-underline"></span>
        </router-link>
        <router-link to="/contact" class="nav-link" @click="closeMenu">
          <span class="link-text">Kontak</span>
          <span class="link-underline"></span>
        </router-link>
      </div>
             
      <div class="nav-toggle" @click="toggleMenu" :class="{ active: isOpen }">
        <span class="bar"></span>
        <span class="bar"></span>
        <span class="bar"></span>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: 'NavBar',
  data() {
    return {
      isOpen: false
    }
  },
  methods: {
    toggleMenu() {
      this.isOpen = !this.isOpen
    },
    closeMenu() {
      this.isOpen = false
    }
  }
}
</script>

<style scoped>
.navbar {
  background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
  backdrop-filter: blur(10px);
  border-bottom: 1px solid rgba(255, 255, 255, 0.1);
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
  position: sticky;
  top: 0;
  z-index: 1000;
}

.nav-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 1.2rem 2rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}

.nav-logo-link {
  text-decoration: none;
  color: white;
  transition: transform 0.3s ease;
}

.nav-logo-link:hover {
  transform: scale(1.05);
}

.logo-content {
  display: flex;
  align-items: center;
  gap: 0.8rem;
}

.logo-icon {
  font-size: 2rem;
  filter: drop-shadow(0 0 10px rgba(255, 255, 255, 0.3));
  animation: float 3s ease-in-out infinite;
}

@keyframes float {
  0%, 100% { transform: translateY(0px); }
  50% { transform: translateY(-5px); }
}

.nav-logo h2 {
  margin: 0;
  font-size: 1.8rem;
  font-weight: 700;
  background: linear-gradient(45deg, #00d4ff, #ff6b9d, #c471ed);
  background-size: 200% 200%;
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: gradientShift 4s ease infinite;
}

@keyframes gradientShift {
  0% { background-position: 0% 50%; }
  50% { background-position: 100% 50%; }
  100% { background-position: 0% 50%; }
}

.nav-menu {
  display: flex;
  gap: 3rem;
  list-style: none;
}

.nav-link {
  position: relative;
  color: rgba(255, 255, 255, 0.9);
  text-decoration: none;
  font-weight: 600;
  padding: 0.8rem 1.5rem;
  border-radius: 12px;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  overflow: hidden;
}

.nav-link::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(255, 255, 255, 0.2), transparent);
  transition: left 0.6s;
}

.nav-link:hover::before {
  left: 100%;
}

.link-text {
  position: relative;
  z-index: 2;
}

.link-underline {
  position: absolute;
  bottom: 8px;
  left: 50%;
  width: 0;
  height: 3px;
  background: linear-gradient(90deg, #00d4ff, #ff6b9d);
  border-radius: 2px;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  transform: translateX(-50%);
}

.nav-link:hover,
.nav-link.router-link-active {
  color: white;
  background: rgba(255, 255, 255, 0.1);
  transform: translateY(-3px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.3);
}

.nav-link:hover .link-underline,
.nav-link.router-link-active .link-underline {
  width: 80%;
}

.nav-toggle {
  display: none;
  flex-direction: column;
  cursor: pointer;
  padding: 0.5rem;
  border-radius: 8px;
  transition: all 0.3s ease;
}

.nav-toggle:hover {
  background: rgba(255, 255, 255, 0.1);
}

.bar {
  width: 28px;
  height: 3px;
  background: linear-gradient(90deg, #00d4ff, #ff6b9d);
  margin: 4px 0;
  transition: all 0.4s cubic-bezier(0.4, 0, 0.2, 1);
  border-radius: 3px;
  transform-origin: center;
}

.nav-toggle.active .bar:nth-child(1) {
  transform: rotate(45deg) translate(8px, 8px);
}

.nav-toggle.active .bar:nth-child(2) {
  opacity: 0;
  transform: scale(0);
}

.nav-toggle.active .bar:nth-child(3) {
  transform: rotate(-45deg) translate(8px, -8px);
}

@media screen and (max-width: 768px) {
  .nav-container {
    padding: 1rem 1.5rem;
  }

  .nav-menu {
    position: fixed;
    left: -100%;
    top: 80px;
    flex-direction: column;
    background: linear-gradient(135deg, #1a1a2e 0%, #16213e 50%, #0f3460 100%);
    backdrop-filter: blur(20px);
    width: 100%;
    text-align: center;
    transition: all 0.5s cubic-bezier(0.4, 0, 0.2, 1);
    padding: 3rem 0;
    gap: 0;
    border-top: 1px solid rgba(255, 255, 255, 0.1);
    box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
  }

  .nav-menu.active {
    left: 0;
  }

  .nav-link {
    display: block;
    margin: 1.5rem 0;
    padding: 1rem 2rem;
    border-radius: 15px;
    font-size: 1.1rem;
  }

  .nav-toggle {
    display: flex;
  }

  .logo-content {
    gap: 0.5rem;
  }

  .logo-icon {
    font-size: 1.8rem;
  }

  .nav-logo h2 {
    font-size: 1.6rem;
  }
}

@media screen and (max-width: 480px) {
  .nav-container {
    padding: 1rem;
  }
  
  .nav-logo h2 {
    font-size: 1.4rem;
  }
  
  .logo-icon {
    font-size: 1.6rem;
  }
}
</style>