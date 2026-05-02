<template>
  <div class="side-nav">
    <button
      class="side-nav-btn back-to-top"
      :class="{ visible: showBackToTop }"
      @click="scrollToTop"
      title="返回顶部"
    >
      ↑
    </button>
    <button
      class="side-nav-btn quick-menu-btn"
      :class="{ active: showMenu }"
      @click="toggleMenu"
      title="快速导航"
    >
      ☰
    </button>
    <transition name="slide">
      <div v-if="showMenu" class="quick-nav-menu">
        <a
          v-for="(item, index) in navItems"
          :key="index"
          :href="item.href"
          class="quick-nav-item"
          @click="scrollToSection(item.href)"
        >
          <span class="nav-icon">{{ item.icon }}</span>
          <span class="nav-label">{{ item.label }}</span>
        </a>
      </div>
    </transition>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const showBackToTop = ref(false)
const showMenu = ref(false)

const navItems = [
  { href: '#about', label: '关于我', icon: '👤' },
  { href: '#timeline', label: '时间线', icon: '📅' },
  { href: '#coding-journey', label: '编程之路', icon: '💻' },
  { href: '#qualities', label: '品质', icon: '⭐' },
  { href: '#achievements', label: '成就', icon: '🏆' },
  { href: '#bookmarks', label: '收藏', icon: '🔖' },
  { href: '#skills', label: '服务', icon: '🛠️' },
  { href: '#contact', label: '联系', icon: '📧' }
]

const handleScroll = () => {
  showBackToTop.value = window.scrollY > 500
}

const scrollToTop = () => {
  window.scrollTo({ top: 0, behavior: 'smooth' })
  showMenu.value = false
}

const toggleMenu = () => {
  showMenu.value = !showMenu.value
}

const scrollToSection = (href) => {
  showMenu.value = false
  const element = document.querySelector(href)
  if (element) {
    const headerOffset = 80
    const elementPosition = element.getBoundingClientRect().top
    const offsetPosition = elementPosition + window.pageYOffset - headerOffset
    window.scrollTo({ top: offsetPosition, behavior: 'smooth' })
  }
}

onMounted(() => {
  window.addEventListener('scroll', handleScroll)
})

onUnmounted(() => {
  window.removeEventListener('scroll', handleScroll)
})
</script>

<style scoped>
.side-nav {
  position: fixed;
  right: 20px;
  bottom: 20px;
  z-index: 1000;
  display: flex;
  flex-direction: column;
  gap: 10px;
}

.side-nav-btn {
  width: 50px;
  height: 50px;
  border-radius: 50%;
  border: none;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  color: white;
  font-size: 1.5rem;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: center;
  box-shadow: 0 4px 15px rgba(99, 102, 241, 0.4);
  transition: all 0.3s ease;
}

.back-to-top {
  opacity: 0;
  visibility: hidden;
  transform: scale(0.8);
}

.back-to-top.visible {
  opacity: 1;
  visibility: visible;
  transform: scale(1);
}

.side-nav-btn:hover {
  transform: scale(1.1);
  box-shadow: 0 6px 20px rgba(99, 102, 241, 0.6);
}

.quick-menu-btn {
  background: linear-gradient(135deg, var(--accent-color), #059669);
}

.quick-nav-menu {
  position: absolute;
  right: 60px;
  bottom: 0;
  background: rgba(17, 24, 39, 0.95);
  backdrop-filter: blur(10px);
  border-radius: 12px;
  border: 1px solid rgba(99, 102, 241, 0.2);
  padding: 12px;
  min-width: 180px;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.3);
}

.quick-nav-item {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 10px 12px;
  color: var(--text-dark);
  text-decoration: none;
  border-radius: 8px;
  transition: all 0.2s ease;
  font-size: 0.9rem;
}

.quick-nav-item:hover {
  background: rgba(99, 102, 241, 0.2);
  color: var(--primary-color);
}

.nav-icon {
  font-size: 1.2rem;
}

.nav-label {
  font-weight: 500;
}

.slide-enter-active,
.slide-leave-active {
  transition: all 0.3s ease;
}

.slide-enter-from,
.slide-leave-to {
  opacity: 0;
  transform: translateX(20px);
}

@media (max-width: 768px) {
  .side-nav {
    right: 10px;
    bottom: 10px;
  }

  .side-nav-btn {
    width: 45px;
    height: 45px;
    font-size: 1.3rem;
  }

  .quick-nav-menu {
    right: 55px;
    min-width: 160px;
  }
}
</style>
