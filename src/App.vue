<template>
  <div class="app">
    <div v-if="isLoading" class="loading-screen">
      <div class="loading-content">
        <div class="logo-container">
          <div class="logo-ring"></div>
          <div class="logo-ring logo-ring-2"></div>
          <div class="logo-initials">柯</div>
        </div>
        <h2 class="loading-title">柯的个人网站</h2>
        <p class="loading-subtitle">正在加载精彩内容...</p>
        <div class="progress-bar">
          <div class="progress-fill" :style="{ width: progress + '%' }"></div>
        </div>
      </div>
    </div>
    <div v-else class="app-content">
      <Header />
      <main>
        <AboutSection />
        <TimelineSection />
        <CodingJourneySection />
        <QualitiesSection />
        <AchievementsSection />
        <BookmarksSection />
        <SkillsSection />
        <ContactSection />
      </main>
      <Footer />
      <SideNav />
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'
import Header from './components/Header.vue'
import AboutSection from './components/AboutSection.vue'
import CodingJourneySection from './components/CodingJourneySection.vue'
import TimelineSection from './components/TimelineSection.vue'
import AchievementsSection from './components/AchievementsSection.vue'
import QualitiesSection from './components/QualitiesSection.vue'
import BookmarksSection from './components/BookmarksSection.vue'
import SkillsSection from './components/SkillsSection.vue'
import ContactSection from './components/ContactSection.vue'
import Footer from './components/Footer.vue'
import SideNav from './components/SideNav.vue'

const isLoading = ref(true)
const progress = ref(0)

onMounted(() => {
  const progressInterval = setInterval(() => {
    if (progress.value < 90) {
      progress.value += Math.random() * 25
    }
  }, 80)

  window.addEventListener('load', () => {
    completeLoading()
  })

  setTimeout(() => {
    completeLoading()
  }, 1200)

  function completeLoading() {
    clearInterval(progressInterval)
    progress.value = 100
    setTimeout(() => {
      isLoading.value = false
    }, 200)
  }
})
</script>

<style scoped>
.app {
  min-height: 100vh;
  display: flex;
  flex-direction: column;
  background: linear-gradient(180deg, var(--bg-darker) 0%, var(--bg-dark) 100%);
  position: relative;
}

/* 加载屏幕 */
.loading-screen {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(135deg, #0f172a 0%, #1e293b 50%, #0f172a 100%);
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 9999;
  animation: fadeIn 0.3s ease;
}

@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

.loading-content {
  text-align: center;
  animation: slideUp 0.5s ease;
}

@keyframes slideUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.logo-container {
  position: relative;
  width: 120px;
  height: 120px;
  margin: 0 auto 2rem;
}

.logo-ring {
  position: absolute;
  width: 100%;
  height: 100%;
  border: 3px solid transparent;
  border-top-color: var(--primary-color);
  border-radius: 50%;
  animation: spin 1.5s linear infinite;
}

.logo-ring-2 {
  width: 90%;
  height: 90%;
  top: 5%;
  left: 5%;
  border-top-color: var(--secondary-color);
  animation: spin 2s linear infinite reverse;
}

@keyframes spin {
  to { transform: rotate(360deg); }
}

.logo-initials {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-size: 3rem;
  font-weight: 700;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  text-shadow: 0 0 30px rgba(0, 240, 255, 0.3);
}

.loading-title {
  font-size: 1.75rem;
  font-weight: 700;
  color: var(--text-dark);
  margin-bottom: 0.5rem;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.loading-subtitle {
  font-size: 0.95rem;
  color: var(--text-light);
  margin-bottom: 2rem;
}

.progress-bar {
  width: 200px;
  height: 4px;
  background: rgba(255, 255, 255, 0.1);
  border-radius: 2px;
  overflow: hidden;
  margin: 0 auto;
}

.progress-fill {
  height: 100%;
  background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
  border-radius: 2px;
  transition: width 0.3s ease;
  box-shadow: 0 0 10px rgba(0, 240, 255, 0.5);
}

.app-content {
  flex: 1;
  display: flex;
  flex-direction: column;
  animation: contentFadeIn 0.5s ease;
}

@keyframes contentFadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

main {
  flex: 1;
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 20px;
  width: 100%;
  position: relative;
  z-index: 10;
}

section {
  padding: 80px 0;
  position: relative;
}

section::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: linear-gradient(180deg, transparent 0%, rgba(17, 24, 39, 0.5) 100%);
  pointer-events: none;
}

section:last-child {
  border-bottom: none;
}
</style>
