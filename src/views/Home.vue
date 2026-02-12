<template>
  <div class="home">
    <section class="hero">
      <div class="hero-content">
        <h1 class="hero-title">欢迎来到我的工具箱</h1>
        <p class="hero-subtitle">这里收集了我开发的各种实用小工具，全部免费下载使用</p>
        <button class="btn hero-btn" @click="$emit('navigate', 'tools')">
          🚀 浏览工具
        </button>
      </div>
    </section>
    
    <section class="features">
      <div class="container">
        <h2 class="section-title">为什么选择我的工具？</h2>
        <div class="features-grid">
          <div class="feature-item">
            <span class="feature-icon">💰</span>
            <h3>完全免费</h3>
            <p>所有工具完全免费，无任何隐藏收费</p>
          </div>
          <div class="feature-item">
            <span class="feature-icon">🔒</span>
            <h3>安全可靠</h3>
            <p>开源代码，无病毒无广告，放心使用</p>
          </div>
          <div class="feature-item">
            <span class="feature-icon">⚡</span>
            <h3>轻量高效</h3>
            <p>体积小巧，运行流畅，不占系统资源</p>
          </div>
        </div>
      </div>
    </section>
    
    <section class="cta">
      <div class="container">
        <p class="cta-text">有问题或建议？欢迎联系我！</p>
      </div>
    </section>
  </div>
</template>

<script>
export default {
  name: 'Home',
  emits: ['navigate']
}
</script>

<style scoped>
.hero {
  background: linear-gradient(135deg, var(--primary-color), #2ecc71);
  color: white;
  padding: 80px 20px;
  text-align: center;
}

.hero-content {
  max-width: 600px;
  margin: 0 auto;
}

.hero-title {
  font-size: 42px;
  font-weight: 700;
  margin-bottom: 20px;
}

.hero-subtitle {
  font-size: 18px;
  opacity: 0.9;
  margin-bottom: 32px;
}

.hero-btn {
  background-color: white;
  color: var(--primary-color);
  font-size: 18px;
  padding: 14px 32px;
}

.hero-btn:hover {
  background-color: var(--bg-color);
}

.features {
  padding: 60px 0;
}

.section-title {
  text-align: center;
  font-size: 28px;
  margin-bottom: 40px;
  color: var(--text-color);
}

.features-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 30px;
}

.feature-item {
  background-color: var(--card-bg);
  padding: 32px 24px;
  border-radius: var(--radius);
  text-align: center;
  box-shadow: var(--shadow);
  transition: transform 0.3s;
}

.feature-item:hover {
  transform: translateY(-4px);
}

.feature-icon {
  font-size: 40px;
  display: block;
  margin-bottom: 16px;
}

.feature-item h3 {
  font-size: 18px;
  margin-bottom: 12px;
  color: var(--text-color);
}

.feature-item p {
  color: var(--text-secondary);
  font-size: 14px;
}

.cta {
  background-color: var(--card-bg);
  padding: 40px 0;
  text-align: center;
}

.cta-text {
  color: var(--text-secondary);
  font-size: 16px;
}

@media (max-width: 768px) {
  .hero-title {
    font-size: 28px;
  }
  
  .hero-subtitle {
    font-size: 16px;
  }
  
  .features-grid {
    grid-template-columns: 1fr;
    gap: 20px;
  }
}
</style>
