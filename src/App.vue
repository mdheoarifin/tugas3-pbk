<template>
  <div id="app">
    <NavBar />
    <router-view />
    <FooterSection />
  </div>
</template>

<script>
import NavBar from '../components/NavBar.vue'
import FooterSection from './components/Footer.vue'

export default {
  name: 'App',
  components: {
    NavBar,
    FooterSection
  }
}
</script>

<style>
#app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
}

main {
  flex: 1;
}
</style>