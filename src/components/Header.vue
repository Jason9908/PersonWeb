<template>
  <header class="header">
    <nav class="nav">
      <div class="nav-brand">
        <a href="#about">柯柯的网站</a>
      </div>
      <ul class="nav-menu" :class="{ 'menu-open': isMenuOpen }">
        <li class="nav-item">
          <a href="#about" class="nav-link" @click="closeMenu">关于我</a>
        </li>
        <li class="nav-item">
          <a href="#timeline" class="nav-link" @click="closeMenu">人生大事记</a>
        </li>
        <li class="nav-item">
          <a href="#coding-journey" class="nav-link" @click="closeMenu">编程来时路</a>
        </li>
        <li class="nav-item">
          <a href="#achievements" class="nav-link" @click="closeMenu">成就</a>
        </li>
        <li class="nav-item">
          <a href="#qualities" class="nav-link" @click="closeMenu">品质</a>
        </li>
        <li class="nav-item">
          <a href="#bookmarks" class="nav-link" @click="closeMenu">收藏</a>
        </li>
        <li class="nav-item">
          <a href="#skills" class="nav-link" @click="closeMenu">服务</a>
        </li>
        <li class="nav-item">
          <a href="#contact" class="nav-link" @click="closeMenu">联系</a>
        </li>
      </ul>
      <button class="menu-toggle" :class="{ active: isMenuOpen }" @click="toggleMenu" aria-label="Toggle menu">
        <span></span>
        <span></span>
        <span></span>
      </button>
    </nav>
  </header>
</template>

<script setup>
import { ref } from 'vue'

const isMenuOpen = ref(false)

const toggleMenu = () => {
  isMenuOpen.value = !isMenuOpen.value
}

const closeMenu = () => {
  isMenuOpen.value = false
}
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

.menu-toggle {
  display: none;
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
  .menu-toggle {
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    width: 30px;
    height: 25px;
    background: transparent;
    border: none;
    cursor: pointer;
    padding: 0;
    z-index: 1001;
  }

  .menu-toggle span {
    width: 100%;
    height: 3px;
    background: var(--primary-color);
    border-radius: 3px;
    transition: all 0.3s ease;
    box-shadow: 0 0 5px rgba(0, 240, 255, 0.5);
  }

  .menu-toggle span:nth-child(1) {
    transform-origin: left center;
  }

  .menu-toggle span:nth-child(3) {
    transform-origin: left center;
  }

  .menu-toggle.active span:nth-child(1) {
    transform: rotate(45deg);
  }

  .menu-toggle.active span:nth-child(2) {
    opacity: 0;
  }

  .menu-toggle.active span:nth-child(3) {
    transform: rotate(-45deg);
  }

  .nav-menu {
    position: fixed;
    top: 0;
    right: -100%;
    width: 70%;
    max-width: 300px;
    height: 100vh;
    background: linear-gradient(180deg, rgba(10, 14, 39, 0.98), rgba(5, 10, 30, 0.98));
    backdrop-filter: blur(20px);
    flex-direction: column;
    padding: 80px 2rem 2rem;
    gap: 0;
    transition: right 0.3s ease;
    box-shadow: -5px 0 20px rgba(0, 0, 0, 0.5);
    border-left: 1px solid rgba(0, 240, 255, 0.2);
  }

  .nav-menu.menu-open {
    right: 0;
  }

  .nav-item {
    width: 100%;
    border-bottom: 1px solid rgba(0, 240, 255, 0.1);
  }

  .nav-link {
    display: block;
    padding: 1rem 0;
    font-size: 1.1rem;
  }

  .nav-brand a {
    font-size: 1.2rem;
  }
}

@media (max-width: 480px) {
  .nav {
    padding: 0.8rem 15px;
  }

  .nav-brand a {
    font-size: 1.1rem;
  }

  .nav-menu {
    width: 80%;
    padding: 70px 1.5rem 2rem;
  }

  .nav-link {
    font-size: 1rem;
    padding: 0.8rem 0;
  }

  .menu-toggle {
    width: 25px;
    height: 20px;
  }

  .menu-toggle span {
    height: 2.5px;
  }
}

/* 菜单遮罩 */
.nav-menu::before {
  content: '';
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  background: rgba(0, 0, 0, 0.5);
  opacity: 0;
  visibility: hidden;
  transition: all 0.3s ease;
  z-index: -1;
}

.nav-menu.menu-open::before {
  opacity: 1;
  visibility: visible;
}
</style>
