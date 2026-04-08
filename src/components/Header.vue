<template>
  <header class="header">
    <nav class="nav">
      <div class="nav-brand">
        <a href="#about">柯柯的网站</a>
      </div>
      <ul class="nav-menu">
        <li class="nav-item">
          <a href="#about" class="nav-link">关于我</a>
        </li>
        <li class="nav-item">
          <a href="#timeline" class="nav-link">人生大事记</a>
        </li>
        <li class="nav-item">
          <a href="#coding-journey" class="nav-link">编程来时路</a>
        </li>
        <li class="nav-item">
          <a href="#achievements" class="nav-link">成就</a>
        </li>
        <li class="nav-item">
          <a href="#qualities" class="nav-link">品质</a>
        </li>
        <li class="nav-item">
          <a href="#bookmarks" class="nav-link">收藏</a>
        </li>
        <li class="nav-item">
          <a href="#skills" class="nav-link">服务</a>
        </li>
        <li class="nav-item">
          <a href="#contact" class="nav-link">联系</a>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script setup>
</script>

<style scoped>
.header {
  background-color: rgba(10, 14, 39, 0.95);
  backdrop-filter: blur(20px);
  box-shadow: 0 4px 20px rgba(0, 0, 0, 0.5);
  border-bottom: 1px solid rgba(0, 240, 255, 0.2);
  position: sticky;
  top: 0;
  z-index: 1000;
}

.nav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 1rem 0;
  max-width: 1200px;
  margin: 0 auto;
  padding: 1rem 20px;
}

.nav-brand a {
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--primary-color);
  text-shadow: var(--glow-text);
  letter-spacing: 1px;
}

.nav-menu {
  display: flex;
  gap: 2rem;
  list-style: none;
}

.nav-link {
  color: var(--text-dark);
  font-weight: 500;
  transition: all 0.3s ease;
  position: relative;
  padding: 0.5rem 0;
}

.nav-link:hover {
  color: var(--primary-color);
  text-shadow: var(--glow-text);
}

.nav-link::after {
  content: '';
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0;
  height: 2px;
  background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
  transition: width 0.3s ease;
  box-shadow: var(--glow);
}

.nav-link:hover::after {
  width: 100%;
}

@media (max-width: 768px) {
  .nav-menu {
    display: none;
  }
}
</style>
