<template>
  <div class="tools-page">
    <div class="container">
      <div class="page-header">
        <h1 class="page-title">工具下载</h1>
        <p class="page-desc">选择你需要的工具，点击下载即可</p>
      </div>
      
      <div class="tools-grid">
        <ToolCard 
          v-for="tool in tools" 
          :key="tool.id" 
          :tool="tool"
        />
      </div>
      
      <div v-if="tools.length === 0" class="empty-state">
        <span class="empty-icon">📦</span>
        <p>暂无工具，敬请期待...</p>
      </div>
    </div>
  </div>
</template>

<script>
import ToolCard from '../components/ToolCard.vue'
import { tools } from '../data/tools.js'

export default {
  name: 'Tools',
  components: {
    ToolCard
  },
  data() {
    return {
      tools: tools
    }
  }
}
</script>

<style scoped>
.tools-page {
  padding: 20px 0;
}

.page-header {
  text-align: center;
  margin-bottom: 40px;
}

.page-title {
  font-size: 32px;
  color: var(--text-color);
  margin-bottom: 12px;
}

.page-desc {
  color: var(--text-secondary);
  font-size: 16px;
}

.tools-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 24px;
}

.empty-state {
  text-align: center;
  padding: 60px 20px;
  color: var(--text-secondary);
}

.empty-icon {
  font-size: 64px;
  display: block;
  margin-bottom: 16px;
}

@media (max-width: 992px) {
  .tools-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 576px) {
  .tools-grid {
    grid-template-columns: 1fr;
  }
  
  .page-title {
    font-size: 24px;
  }
}
</style>
