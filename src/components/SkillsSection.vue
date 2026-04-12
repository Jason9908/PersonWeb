<template>
  <section id="skills" class="services">
    <h2 class="section-title">技术支持服务</h2>
    <p class="section-subtitle">提供专业的技术支持服务，帮你解决各类技术难题</p>
    <div class="services-grid">
      <div
        v-for="(service, index) in services"
        :key="index"
        class="service-card"
      >
        <div class="service-icon">{{ service.icon }}</div>
        <h3 class="service-title">{{ service.title }}</h3>
        <p class="service-description">{{ service.description }}</p>
        <ul class="service-features">
          <li v-for="(feature, i) in service.features" :key="i">{{ feature }}</li>
        </ul>
        <a href="#contact" class="service-link">
          了解更多 <span>→</span>
        </a>
      </div>
    </div>
  </section>
</template>

<script setup>
const services = [
  {
    icon: '🎯',
    title: '全栈开发入门指导',
    description: '涵盖前端与后端基础，助您快速入门',
    features: [
      '前端开发（HTML/CSS/JavaScript/React/Vue）',
      '后端开发（Java/Python/C/C++/嵌入式）',
      '数据库设计与操作',
      '版本控制',
      '项目实战与代码审查'
    ]
  },
  {
    icon: '🔧',
    title: '软件故障排查与优化',
    description: '解决电脑系统、软件的常见问题与性能提升',
    features: [
      'Windows系统优化与故障修复',
      '软件安装失败问题解决',
      '电脑卡顿、蓝屏等故障排查',
      '软件兼容性问题处理',
      '系统性能提升建议',
      '软件平替'
    ]
  },
  {
    icon: '⚙️',
    title: '软件安装与环境配置',
    description: '为您安全、正确地安装并配置各类办公、开发及工具软件',
    features: [
      '开发环境搭建',
      '数据库安装与配置',
      '办公软件安装（Office、WPS等）',
      '工具软件配置',
      '远程部署与环境调试'
    ]
  },
  {
    icon: '🤖',
    title: 'AI应用开发与指导',
    description: '利用AI技术提升开发效率，实现智能应用',
    features: [
      'AI辅助编程',
      '智能聊天机器人开发',
      'AI工具使用指导',
      'AI项目集成',
      'AI模型部署'
    ]
  }
]
</script>

<style scoped>
.services {
  background-color: var(--bg-darker);
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

.services-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(320px, 1fr));
  gap: 2rem;
  margin-top: 3rem;
}

.service-card {
  background: linear-gradient(135deg, var(--bg-card) 0%, rgba(18, 24, 41, 0.6) 100%);
  border-radius: 16px;
  padding: 2rem;
  border: 1px solid rgba(0, 240, 255, 0.1);
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.service-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.3s ease;
  box-shadow: var(--glow);
}

.service-card:hover::before {
  transform: scaleX(1);
}

.service-card:hover {
  transform: translateY(-8px);
  box-shadow: var(--shadow-lg);
  border-color: rgba(0, 240, 255, 0.3);
}

.service-icon {
  font-size: 3rem;
  margin-bottom: 1rem;
  display: inline-block;
  filter: drop-shadow(0 0 10px var(--primary-color));
}

.service-title {
  font-size: 1.5rem;
  font-weight: 700;
  margin-bottom: 0.75rem;
  color: var(--text-dark);
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.service-description {
  color: var(--text-light);
  line-height: 1.7;
  margin-bottom: 1.5rem;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

.service-features {
  list-style: none;
  margin-bottom: 1.5rem;
}

.service-features li {
  padding: 0.5rem 0;
  padding-left: 1.5rem;
  position: relative;
  color: var(--text-dark);
  font-size: 0.95rem;
  text-rendering: optimizeLegibility;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  font-weight: 500;
}

.service-features li::before {
  content: '▹';
  position: absolute;
  left: 0;
  color: var(--primary-color);
  font-weight: bold;
  font-size: 1.2rem;
  text-shadow: var(--glow-text);
}

.service-link {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  color: var(--primary-color);
  font-weight: 600;
  transition: gap 0.3s ease, text-shadow 0.3s ease;
}

.service-link:hover {
  gap: 1rem;
  text-shadow: var(--glow-text);
}

.service-link span {
  transition: transform 0.3s ease;
}

.service-link:hover span {
  transform: translateX(4px);
}

@media (max-width: 768px) {
  .services-grid {
    grid-template-columns: 1fr;
    gap: 1.5rem;
  }

  .service-card {
    padding: 1.5rem;
  }

  .service-icon {
    font-size: 2.5rem;
  }

  .service-title {
    font-size: 1.25rem;
  }
}
</style>
