<template>
  <footer class="footer">
    <div class="container footer-content">
      <p class="copyright">© 2026 我的工具箱 - 个人小工具分享站</p>
      <p class="tech-info">Made with Vue.js ❤️</p>
    </div>
  </footer>
</template>

<script>
export default {
  name: 'Footer'
}
</script>

<style scoped>
.footer {
  background-color: var(--card-bg);
  border-top: 1px solid var(--border-color);
  padding: 24px 0;
  margin-top: auto;
}

.footer-content {
  text-align: center;
}

.copyright {
  color: var(--text-color);
  font-weight: 500;
  margin-bottom: 8px;
}

.tech-info {
  color: var(--text-secondary);
  font-size: 14px;
}
</style>
