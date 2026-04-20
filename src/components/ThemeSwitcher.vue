<template>
  <div class="theme-switcher">
    <h3>主题选择</h3>
    <div class="theme-options">
      <button 
        v-for="theme in themes" 
        :key="theme.id"
        class="theme-option"
        :class="{ active: currentTheme === theme.id }"
        @click="switchTheme(theme.id)"
        :style="{
          backgroundColor: theme.colors['--bg-darker'],
          borderColor: theme.colors['--primary-color'],
          color: theme.colors['--text-dark']
        }"
      >
        <div class="theme-preview">
          <div class="preview-bg" :style="{ backgroundColor: theme.colors['--bg-darker'] }"></div>
          <div class="preview-card" :style="{ backgroundColor: theme.colors['--bg-card'] }"></div>
          <div class="preview-accent" :style="{ backgroundColor: theme.colors['--primary-color'] }"></div>
        </div>
        <span>{{ theme.name }}</span>
      </button>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const themes = [
  {
    id: 'default',
    name: '默认主题',
    colors: {
      '--primary-color': '#0066cc',
      '--primary-color-rgb': '0, 102, 204',
      '--secondary-color': '#004499',
      '--accent-color': '#3399ff',
      '--text-dark': '#333333',
      '--text-light': '#666666',
      '--bg-dark': '#f5f5f5',
      '--bg-darker': '#ffffff',
      '--bg-card': '#ffffff',
      '--shadow': '0 4px 20px rgba(0, 102, 204, 0.1)',
      '--shadow-lg': '0 10px 40px rgba(0, 102, 204, 0.15)',
      '--glow': '0 0 20px rgba(0, 102, 204, 0.3)',
      '--glow-text': '0 0 10px rgba(0, 102, 204, 0.5)'
    }
  },
  {
    id: 'forest',
    name: '森林主题',
    colors: {
      '--primary-color': '#4ade80',
      '--primary-color-rgb': '74, 222, 128',
      '--secondary-color': '#166534',
      '--accent-color': '#bbf7d0',
      '--text-dark': '#ffffff',
      '--text-light': '#dcfce7',
      '--bg-dark': '#064e3b',
      '--bg-darker': '#064e3b',
      '--bg-card': '#15803d',
      '--shadow': '0 4px 20px rgba(74, 222, 128, 0.15)',
      '--shadow-lg': '0 10px 40px rgba(74, 222, 128, 0.25)',
      '--glow': '0 0 20px rgba(74, 222, 128, 0.5)',
      '--glow-text': '0 0 10px rgba(74, 222, 128, 0.8)'
    }
  },
  {
    id: 'ocean',
    name: '海洋主题',
    colors: {
      '--primary-color': '#38bdf8',
      '--primary-color-rgb': '56, 189, 248',
      '--secondary-color': '#0369a1',
      '--accent-color': '#bae6fd',
      '--text-dark': '#ffffff',
      '--text-light': '#e0f2fe',
      '--bg-dark': '#0c4a6e',
      '--bg-darker': '#0c4a6e',
      '--bg-card': '#0ea5e9',
      '--shadow': '0 4px 20px rgba(56, 189, 248, 0.15)',
      '--shadow-lg': '0 10px 40px rgba(56, 189, 248, 0.25)',
      '--glow': '0 0 20px rgba(56, 189, 248, 0.5)',
      '--glow-text': '0 0 10px rgba(56, 189, 248, 0.8)'
    }
  },
  {
    id: 'sunset',
    name: '日落主题',
    colors: {
      '--primary-color': '#fb923c',
      '--primary-color-rgb': '251, 146, 60',
      '--secondary-color': '#c2410c',
      '--accent-color': '#fdba74',
      '--text-dark': '#ffffff',
      '--text-light': '#fef3c7',
      '--bg-dark': '#9a3412',
      '--bg-darker': '#9a3412',
      '--bg-card': '#ea580c',
      '--shadow': '0 4px 20px rgba(251, 146, 60, 0.15)',
      '--shadow-lg': '0 10px 40px rgba(251, 146, 60, 0.25)',
      '--glow': '0 0 20px rgba(251, 146, 60, 0.5)',
      '--glow-text': '0 0 10px rgba(251, 146, 60, 0.8)'
    }
  }
]

const currentTheme = ref('default')

const switchTheme = (themeId) => {
  currentTheme.value = themeId
  const theme = themes.find(t => t.id === themeId)
  if (theme) {
    Object.entries(theme.colors).forEach(([key, value]) => {
      document.documentElement.style.setProperty(key, value)
    })
    localStorage.setItem('theme', themeId)
  }
}

onMounted(() => {
  const savedTheme = localStorage.getItem('theme')
  if (savedTheme && themes.some(t => t.id === savedTheme)) {
    switchTheme(savedTheme)
  }
})
</script>

<style scoped>
.theme-switcher {
  margin: 2rem 0;
}

.theme-switcher h3 {
  font-size: 1.1rem;
  margin-bottom: 1rem;
  font-weight: 600;
  color: var(--primary-color);
}

.theme-options {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}

.theme-option {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 0.5rem;
  padding: 1rem;
  border: 2px solid var(--primary-color);
  border-radius: 8px;
  background-color: var(--bg-darker);
  color: var(--text-dark);
  cursor: pointer;
  transition: all 0.3s ease;
  min-width: 120px;
}

.theme-option:hover {
  transform: translateY(-2px);
  box-shadow: var(--shadow-lg);
}

.theme-option.active {
  box-shadow: var(--glow);
}

.theme-preview {
  position: relative;
  width: 80px;
  height: 60px;
  border-radius: 4px;
  overflow: hidden;
}

.preview-bg {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}

.preview-card {
  position: absolute;
  top: 10px;
  left: 10px;
  width: 60px;
  height: 30px;
  border-radius: 2px;
}

.preview-accent {
  position: absolute;
  bottom: 10px;
  left: 10px;
  width: 40px;
  height: 4px;
  border-radius: 2px;
}

.theme-option span {
  font-size: 0.9rem;
  font-weight: 600;
}

@media (max-width: 768px) {
  .theme-options {
    justify-content: center;
  }
}
</style>