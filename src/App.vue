<template>
  <Header :current-view="currentView" @navigate="navigateTo" />
  <main class="main-content">
    <Home v-if="currentView === 'home'" @navigate="navigateTo" />
    <Tools v-else-if="currentView === 'tools'" @navigate="navigateTo" />
  </main>
  <Footer />
</template>

<script>
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'
import Home from './views/Home.vue'
import Tools from './views/Tools.vue'

export default {
  name: 'App',
  components: {
    Header,
    Footer,
    Home,
    Tools
  },
  data() {
    return {
      currentView: 'home'
    }
  },
  methods: {
    navigateTo(view) {
      this.currentView = view
    }
  }
}
</script>

<style scoped>
.main-content {
  flex: 1;
  padding: 40px 0;
}
</style>
