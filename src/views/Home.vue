<template>
  <div class="home">
    <section class="hero">
      <div class="hero-content">
        <h1 class="hero-title">欢迎来到我的工具箱</h1>
        <p class="hero-subtitle">这里收集了我开发的各种实用小工具，全部免费下载使用</p>
        <button class="btn hero-btn" @click="$emit('navigate', 'tools')">
          🚀 下载
        </button>
      </div>
    </section>
    
    <section class="tools-intro">
      <div class="container">
        <h2 class="section-title">我的工具介绍</h2>
        <div class="tools-grid">
          <template v-for="tool in tools" :key="tool.id">
            <!-- 一级菜单 -->
            <div class="tool-item" :class="{ clickable: tool.subtools && tool.subtools.length > 0 }" @click="tool.subtools && tool.subtools.length > 0 ? toggleSubmenu(tool.id) : null">
              <img src="/image/home.png" alt="工具图标" class="tool-icon-img">
              <div class="tool-info">
                <h3>{{ tool.name }}</h3>
                <p>{{ tool.description }}</p>
              </div>
              <div class="tool-actions">
                <button class="btn download-btn" @click.stop="$emit('navigate', 'tools')" v-if="tool.downloadUrl">⬇ 下载</button>
                <button class="btn demo-btn" @click.stop="showDemo(tool)" v-if="tool.videoUrl">🎬 看演示</button>
              </div>
              <div class="submenu-placeholder" v-if="!tool.subtools || tool.subtools.length === 0"></div>
              <div class="submenu-arrow" :class="{ active: openSubmenu === tool.id }" v-if="tool.subtools && tool.subtools.length > 0">▼</div>
            </div>
            <!-- 二级菜单容器 -->
            <div class="submenu" v-if="openSubmenu === tool.id && tool.subtools && tool.subtools.length > 0">
              <div class="submenu-grid">
                <div class="tool-item sub-tool-item" v-for="(subtool, index) in tool.subtools" :key="'sub-' + index">
                  <img src="/image/home.png" alt="工具图标" class="tool-icon-img">
                  <div class="tool-info">
                    <h3>{{ subtool.name }}</h3>
                    <p>{{ subtool.description }}</p>
                  </div>
                  <button class="btn demo-btn" @click.stop="showDemo(subtool)">
                    🎬 看演示
                  </button>
                </div>
              </div>
            </div>
          </template>
        </div>
      </div>
    </section>
    
    <section class="cta">
      <div class="container">
        <p class="cta-text">有问题或建议？欢迎联系我！</p>
      </div>
    </section>

    <VideoModal 
      :show="showModal" 
      :title="currentTool?.name || '工具演示'"
      :videoUrl="currentTool?.videoUrl || ''"
      @close="closeModal"
    />
  </div>
</template>

<script>
import VideoModal from '../components/VideoModal.vue'

export default {
  name: 'Home',
  components: {
    VideoModal
  },
  emits: ['navigate'],
  data() {
    return {
      showModal: false,
      currentTool: null,
      openSubmenu: null,
      tools: [
        {
          id: 1,
          name: '张裕锋工具集',
          description: 'CAD快速瘦身、布置地面疏散指示、底图处理等9个实用CAD工具集合',
          downloadUrl: './downloads/张裕锋工具集安装包.zip',
          videoUrl: '',
          subtools: [
            { name: '01 CAD快速瘦身', description: '快速减小CAD文件体积', videoUrl: '' },
            { name: '02 布置地面疏散指示', description: '自动布置地面疏散指示标志', videoUrl: '/videos/02.mp4' },
            { name: '03 底图处理', description: '处理CAD底图图层和显示', videoUrl: '/videos/03.mp4' },
            { name: '04 图号文字递增', description: '自动递增图号和文字编号', videoUrl: '/videos/04.mp4' },
            { name: '05 图片去黑框', description: '去除图片黑色边框', videoUrl: '/videos/05.mp4' },
            { name: '06 文字复制', description: '批量复制文字内容', videoUrl: '/videos/06.mp4' },
            { name: '07 图框自动编号', description: '自动为图框编号排序', videoUrl: '/videos/07.mp4' },
            { name: '08 0层置为当前层', description: '将0层设为当前图层', videoUrl: '/videos/08.mp4' },
            { name: '09 开图自动选字体', description: '打开图纸自动选择字体', videoUrl: '/videos/09.mp4' }
          ]
        },
        {
          id: 2,
          name: 'PDSD系统图绘制工具',
          description: '快速绘制PDSD系统图',
          downloadUrl: './downloads/PDSD系统图绘制工具安装包.zip',
          videoUrl: '/videos/PDSD.mp4'
        }
      ]
    }
  },
  methods: {
    showDemo(tool) {
      this.currentTool = tool
      this.showModal = true
    },
    closeModal() {
      this.showModal = false
    },
    toggleSubmenu(toolId) {
      if (this.openSubmenu === toolId) {
        this.openSubmenu = null
      } else {
        this.openSubmenu = toolId
      }
    }
  }
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

.tools-intro {
  padding: 60px 0;
}

.tools-grid {
  display: flex;
  flex-direction: column;
  gap: 20px;
}

.tool-item {
  background-color: var(--card-bg);
  padding: 24px;
  border-radius: var(--radius);
  box-shadow: var(--shadow);
  display: flex;
  align-items: center;
  gap: 20px;
  transition: transform 0.3s;
  position: relative;
}

.tool-item.clickable:hover {
  transform: translateX(4px);
  cursor: pointer;
}

.tool-item:not(.clickable):hover {
  transform: none;
}

.sub-tool-item {
  margin-left: 40px;
  width: calc(100% - 40px);
  background-color: var(--bg-color);
}

.tool-item .tool-icon {
  font-size: 40px;
  flex-shrink: 0;
}

.tool-icon-img {
  width: 60px;
  height: 60px;
  object-fit: contain;
  flex-shrink: 0;
}

.tool-info {
  flex: 1;
}

.tool-info h3 {
  font-size: 18px;
  font-weight: 600;
  color: var(--text-color);
  margin-bottom: 8px;
}

.tool-info p {
  color: var(--text-secondary);
  font-size: 14px;
}

.demo-btn {
  flex-shrink: 0;
  padding: 10px 20px;
  font-size: 14px;
}

.tool-actions {
  display: flex;
  gap: 8px;
  flex-shrink: 0;
}

.download-btn {
  flex-shrink: 0;
  padding: 10px 20px;
  font-size: 14px;
  text-decoration: none;
}

.submenu-arrow {
  flex-shrink: 0;
  width: 20px;
  text-align: center;
  font-size: 12px;
  color: var(--text-secondary);
  transition: transform 0.3s;
  cursor: pointer;
}

.submenu-placeholder {
  flex-shrink: 0;
  width: 20px;
}

.submenu-arrow.active {
  transform: rotate(180deg);
}

.submenu {
  width: 100%;
}

.submenu-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 12px;
  margin-top: 12px;
}

.sub-tool-item {
  background-color: var(--bg-color);
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

  .tools-grid {
    gap: 16px;
  }

  .tool-item {
    flex-direction: column;
    text-align: center;
  }

  .demo-btn {
    width: 100%;
  }
}
</style>
