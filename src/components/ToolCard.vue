<template>
  <div class="tool-card">
    <img :src="tool.iconUrl || '/image/home.png'" alt="工具图标" class="tool-icon">
    <h3 class="tool-name">{{ tool.name }}</h3>
    <p class="tool-desc">{{ tool.description }}</p>
    <div class="tool-meta">
      <span class="tool-version">v{{ tool.version }}</span>
      <span class="tool-size">{{ tool.size }}</span>
    </div>
    <a 
      :href="tool.downloadUrl" 
      class="btn download-btn"
      download
    >
      ⬇️ 下载
    </a>
  </div>
</template>

<script>
export default {
  name: 'ToolCard',
  props: {
    tool: {
      type: Object,
      required: true
    }
  }
}
</script>

<style scoped>
.tool-card {
  background-color: var(--card-bg);
  border-radius: var(--radius);
  padding: 24px;
  box-shadow: var(--shadow);
  transition: all 0.3s;
  display: flex;
  flex-direction: column;
  align-items: center;
  text-align: center;
}

.tool-card:hover {
  transform: translateY(-4px);
  box-shadow: 0 8px 24px rgba(0, 0, 0, 0.15);
}

.tool-icon {
  width: 60px;
  height: 60px;
  object-fit: contain;
  margin-bottom: 16px;
}

.tool-name {
  font-size: 20px;
  font-weight: 600;
  color: var(--text-color);
  margin-bottom: 12px;
}

.tool-desc {
  color: var(--text-secondary);
  font-size: 14px;
  line-height: 1.6;
  margin-bottom: 16px;
  flex: 1;
}

.tool-meta {
  display: flex;
  gap: 16px;
  margin-bottom: 20px;
  font-size: 13px;
  color: var(--text-secondary);
}

.tool-meta span {
  background-color: var(--bg-color);
  padding: 4px 12px;
  border-radius: 20px;
}

.download-btn {
  width: 100%;
}
</style>
