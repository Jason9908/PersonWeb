<template>
  <section id="achievements" class="experience">
    <h2 class="section-title">我的成就</h2>
    <p class="section-subtitle">边学边赚，用技术变现的精彩瞬间</p>
    <div class="achievements-grid">
      <div
        v-for="(achievement, index) in achievements"
        :key="index"
        :class="['achievement-card', achievement.highlight ? 'highlight' : '']"
      >
        <span class="achievement-card-icon">{{ achievement.icon }}</span>
        <h3 class="achievement-card-title">{{ achievement.title }}</h3>
        <p class="achievement-card-desc">{{ achievement.description }}</p>
        <span v-if="achievement.highlight" class="achievement-badge">🔥 精彩</span>
      </div>
    </div>
  </section>
</template>

<script setup>
const achievements = [
  {
    icon: '💰',
    title: '边学边赚',
    description: '30分钟边学边赚C++线程200元',
    highlight: true
  },
  {
    icon: '🖥️',
    title: '私活换设备',
    description: '一单私活赚一个显示屏',
    highlight: true
  },
  {
    icon: '📝',
    title: '坚持创作',
    description: 'CSDN坚持100天发博客，一篇博文赚一个开发板',
    highlight: true
  },
  {
    icon: '👥',
    title: '带团队',
    description: '带15个同学做项目',
    highlight: false
  },
  {
    icon: '⚡',
    title: '高效学习',
    description: '一天完成一周的实训，30分钟高分通过C语言二级',
    highlight: false
  },
  {
    icon: '🎮',
    title: '快速开发',
    description: '两天手撸代码完成EasyX飞机大战',
    highlight: false
  },
  {
    icon: '💻',
    title: '月入设备',
    description: '靠接软件私活一个月换苹果电脑',
    highlight: true
  },
  {
    icon: '🗄️',
    title: '技术变现',
    description: '数据库试卷5个SQL赚50元（别人给80）',
    highlight: false
  },
  {
    icon: '🚀',
    title: '远程部署',
    description: '一个远程部署就150到手',
    highlight: false
  },
  {
    icon: '🌐',
    title: '项目交付',
    description: '一个Flask项目6个网页500元',
    highlight: true
  },
  {
    icon: '🎯',
    title: 'CSDN成就',
    description: '8K粉丝账号：Jasonakeke',
    highlight: true
  },
  {
    icon: '📢',
    title: '公众号',
    description: 'Jasonakeke - 分享技术与变现',
    highlight: true
  },
  {
    icon: '🌐',
    title: '网站升级',
    description: '个人网站全面升级，添加AI功能和更多内容',
    highlight: true
  }
]
</script>

<style scoped>
.experience {
  background-color: var(--bg-dark);
}

.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 1rem;
  color: var(--text-dark);
  text-align: center;
  text-shadow: var(--glow-text);
  letter-spacing: 2px;
}

.section-subtitle {
  font-size: 1.1rem;
  color: var(--text-light);
  text-align: center;
  margin-bottom: 3rem;
  max-width: 600px;
  margin-left: auto;
  margin-right: auto;
}

.achievements-grid {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(280px, 1fr));
  gap: 1.5rem;
  margin-top: 3rem;
}

.achievement-card {
  background: linear-gradient(135deg, var(--bg-card) 0%, rgba(18, 24, 41, 0.8) 100%);
  border-radius: 16px;
  padding: 1.75rem;
  border: 1px solid rgba(0, 240, 255, 0.1);
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
}

.achievement-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 3px;
  background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.3s ease;
  box-shadow: var(--glow);
}

.achievement-card:hover::before {
  transform: scaleX(1);
}

.achievement-card:hover {
  transform: translateY(-6px);
  box-shadow: var(--shadow-lg);
  border-color: rgba(0, 240, 255, 0.3);
}

.achievement-card.highlight {
  border: 2px solid rgba(245, 158, 11, 0.3);
  background: linear-gradient(135deg, rgba(245, 158, 11, 0.1) 0%, var(--bg-card) 100%);
}

.achievement-card.highlight:hover {
  border-color: rgba(245, 158, 11, 0.5);
  box-shadow: 0 0 30px rgba(245, 158, 11, 0.2);
}

.achievement-card-icon {
  font-size: 2.5rem;
  display: block;
  margin-bottom: 1rem;
  filter: drop-shadow(0 0 10px currentColor);
}

.achievement-card-title {
  font-size: 1.25rem;
  font-weight: 700;
  margin-bottom: 0.75rem;
  color: var(--text-dark);
}

.achievement-card-desc {
  color: var(--text-light);
  line-height: 1.6;
  font-size: 0.95rem;
}

.achievement-badge {
  position: absolute;
  top: 1rem;
  right: 1rem;
  background: linear-gradient(135deg, #f59e0b, #ef4444);
  color: white;
  padding: 0.25rem 0.75rem;
  border-radius: 20px;
  font-size: 0.75rem;
  font-weight: 600;
  box-shadow: 0 0 15px rgba(245, 158, 11, 0.4);
}

@media (max-width: 768px) {
  .achievements-grid {
    grid-template-columns: 1fr;
    gap: 1rem;
  }

  .achievement-card {
    padding: 1.5rem;
  }

  .achievement-card-icon {
    font-size: 2rem;
  }

  .achievement-card-title {
    font-size: 1.1rem;
  }
}
</style>
