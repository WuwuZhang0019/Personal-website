<template>
  <header class="header">
    <div class="container header-content">
      <div class="logo" @click="$emit('navigate', 'home')">
        <span class="logo-icon">🛠️</span>
        <span class="logo-text">我的工具箱</span>
      </div>
      <nav class="nav">
        <a 
          class="nav-link" 
          :class="{ active: currentView === 'home' }"
          @click="$emit('navigate', 'home')"
        >
          首页
        </a>
        <a 
          class="nav-link" 
          :class="{ active: currentView === 'tools' }"
          @click="$emit('navigate', 'tools')"
        >
          工具下载
        </a>
      </nav>
    </div>
  </header>
</template>

<script>
export default {
  name: 'Header',
  props: {
    currentView: {
      type: String,
      default: 'home'
    }
  },
  emits: ['navigate']
}
</script>

<style scoped>
.header {
  background-color: var(--card-bg);
  box-shadow: var(--shadow);
  position: sticky;
  top: 0;
  z-index: 100;
}

.header-content {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 16px 20px;
}

.logo {
  display: flex;
  align-items: center;
  gap: 10px;
  cursor: pointer;
  transition: transform 0.3s;
}

.logo:hover {
  transform: scale(1.02);
}

.logo-icon {
  font-size: 28px;
}

.logo-text {
  font-size: 20px;
  font-weight: 700;
  color: var(--text-color);
}

.nav {
  display: flex;
  gap: 24px;
}

.nav-link {
  color: var(--text-secondary);
  font-weight: 500;
  cursor: pointer;
  padding: 8px 16px;
  border-radius: 8px;
  transition: all 0.3s;
}

.nav-link:hover,
.nav-link.active {
  color: var(--primary-color);
  background-color: rgba(52, 152, 219, 0.1);
}

@media (max-width: 480px) {
  .logo-text {
    font-size: 16px;
  }
  
  .nav {
    gap: 12px;
  }
  
  .nav-link {
    padding: 6px 12px;
    font-size: 14px;
  }
}
</style>
