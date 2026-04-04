<template>
  <footer class="footer">
    <div class="footer-content">
      <div class="footer-section">
        <h3>关于</h3>
        <p>
          柯柯 - CSDN全栈领域新星博主、阿里云专家、工信部认证物联网技术开发工程师。
          热爱分享技术，带你一起边学边赚！
        </p>
      </div>
      <div class="footer-section">
        <h3>快速链接</h3>
        <ul>
          <li><a href="#about">关于我</a></li>
          <li><a href="#timeline">人生时间线</a></li>
          <li><a href="#achievements">我的成就</a></li>
          <li><a href="#qualities">人格特质</a></li>
          <li><a href="#bookmarks">收藏网站</a></li>
          <li><a href="#skills">技术支持服务</a></li>
          <li><a href="#contact">联系</a></li>
        </ul>
      </div>
      <div class="footer-section">
        <h3>关注我</h3>
        <ul>
          <li><a href="https://Jasonakeke.blog.csdn.net" target="_blank" rel="noopener noreferrer">CSDN: Jasonakeke</a></li>
          <li><a href="#contact">公众号: Jasonakeke (扫码)</a></li>
          <li><a href="#contact">微信: (扫码添加)</a></li>
        </ul>
      </div>
    </div>
    <div class="footer-bottom">
      <p>&copy; {{ currentYear }} 柯柯的网站. 边学边赚，一起成长！</p>
    </div>
  </footer>
</template>

<script setup>
import { computed } from 'vue'

const currentYear = computed(() => new Date().getFullYear())
</script>

<style scoped>
.footer {
  background: linear-gradient(180deg, var(--bg-darker) 0%, #02040a 100%);
  color: white;
  margin-top: auto;
  border-top: 1px solid rgba(0, 240, 255, 0.2);
}

.footer-content {
  max-width: 1200px;
  margin: 0 auto;
  padding: 3rem 20px;
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 2rem;
}

.footer-section h3 {
  font-size: 1.1rem;
  margin-bottom: 1rem;
  font-weight: 600;
  color: var(--primary-color);
  text-shadow: var(--glow-text);
}

.footer-section p {
  color: var(--text-light);
  line-height: 1.7;
}

.footer-section ul {
  list-style: none;
}

.footer-section ul li {
  margin-bottom: 0.5rem;
}

.footer-section ul li a {
  color: var(--text-light);
  transition: color 0.3s ease, text-shadow 0.3s ease;
}

.footer-section ul li a:hover {
  color: var(--primary-color);
  text-shadow: var(--glow-text);
}

.footer-bottom {
  background: rgba(0, 0, 0, 0.3);
  padding: 1.5rem 20px;
  text-align: center;
  display: flex;
  justify-content: center;
  gap: 2rem;
  flex-wrap: wrap;
  border-top: 1px solid rgba(0, 240, 255, 0.1);
}

.footer-bottom p {
  color: var(--text-light);
  font-size: 0.9rem;
}

@media (max-width: 768px) {
  .footer-content {
    grid-template-columns: 1fr;
    gap: 2rem;
    padding: 2rem 20px;
  }

  .footer-bottom {
    flex-direction: column;
    gap: 0.5rem;
  }
}
</style>
