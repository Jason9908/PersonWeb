<template>
  <section id="projects" class="projects">
    <div class="container">
      <div class="section-header">
        <h2 class="section-title">精选项目</h2>
        <p class="section-subtitle">展示我的技术实力</p>
      </div>
      <div class="projects-grid">
        <div
          v-for="project in projects"
          :key="project.title"
          class="project-card"
        >
          <div class="project-image">
            <div class="image-placeholder">
              <span class="project-icon">{{ project.icon }}</span>
            </div>
            <div class="project-overlay">
              <div class="project-links">
                <a v-if="project.github" :href="project.github" class="project-link" target="_blank">
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="currentColor">
                    <path d="M12 0C5.374 0 0 5.373 0 12c0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23A11.509 11.509 0 0112 5.803c1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576C20.566 21.797 24 17.3 24 12c0-6.627-5.373-12-12-12z"/>
                  </svg>
                </a>
                <a v-if="project.demo" :href="project.demo" class="project-link" target="_blank">
                  <svg width="20" height="20" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
                    <path d="M18 13v6a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V8a2 2 0 0 1 2-2h6"/>
                    <polyline points="15 3 21 3 21 9"/>
                    <line x1="10" y1="14" x2="21" y2="3"/>
                  </svg>
                </a>
              </div>
            </div>
          </div>
          <div class="project-content">
            <h3 class="project-title">{{ project.title }}</h3>
            <p class="project-description">{{ project.description }}</p>
            <div class="project-tags">
              <span
                v-for="tag in project.tags"
                :key="tag"
                class="project-tag"
              >
                {{ tag }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
const projects = [
  {
    title: '电商平台',
    description: '一个功能完整的现代化电商平台，支持商品管理、购物车、支付集成等功能。',
    icon: '🛒',
    tags: ['Vue 3', 'TypeScript', 'Node.js', 'PostgreSQL'],
    github: '#',
    demo: '#'
  },
  {
    title: '任务管理系统',
    description: '团队协作任务管理工具，支持看板视图、任务分配、进度追踪等功能。',
    icon: '📋',
    tags: ['React', 'GraphQL', 'MongoDB', 'Express'],
    github: '#',
    demo: '#'
  },
  {
    title: '数据可视化仪表板',
    description: '实时数据监控和分析平台，提供丰富的图表和交互式数据展示。',
    icon: '📊',
    tags: ['Vue', 'D3.js', 'WebSocket', 'Redis'],
    github: '#',
    demo: '#'
  },
  {
    title: '社交媒体应用',
    description: '现代化的社交媒体平台，支持动态发布、实时聊天、好友互动等功能。',
    icon: '💬',
    tags: ['React', 'Socket.io', 'AWS', 'Docker'],
    github: '#',
    demo: '#'
  },
  {
    title: 'AI 辅助写作工具',
    description: '集成 AI 能力的智能写作助手，提供文本生成、语法检查、风格优化等功能。',
    icon: '✨',
    tags: ['Vue', 'Python', 'OpenAI API', 'FastAPI'],
    github: '#',
    demo: '#'
  },
  {
    title: '在线学习平台',
    description: '综合性在线教育平台，支持课程管理、在线视频、作业提交等功能。',
    icon: '🎓',
    tags: ['Next.js', 'PostgreSQL', 'Vercel', 'Stripe'],
    github: '#',
    demo: '#'
  }
]
</script>

<style scoped>
.projects {
  padding: 6rem 2rem;
}

.section-header {
  text-align: center;
  margin-bottom: 4rem;
}

.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 1rem;
  background: linear-gradient(135deg, #fff 0%, #00d4ff 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.section-subtitle {
  color: #7c3aed;
  font-size: 1.1rem;
}

.projects-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(350px, 1fr));
  gap: 2rem;
}

.project-card {
  background: rgba(30, 30, 45, 0.8);
  border-radius: 16px;
  overflow: hidden;
  border: 1px solid rgba(255, 255, 255, 0.1);
  transition: all 0.3s ease;
}

.project-card:hover {
  transform: translateY(-8px);
  border-color: rgba(124, 58, 237, 0.5);
  box-shadow: 0 25px 50px rgba(124, 58, 237, 0.2);
}

.project-image {
  position: relative;
  height: 200px;
  overflow: hidden;
}

.image-placeholder {
  width: 100%;
  height: 100%;
  background: linear-gradient(135deg, rgba(124, 58, 237, 0.2), rgba(0, 212, 255, 0.2));
  display: flex;
  align-items: center;
  justify-content: center;
}

.project-icon {
  font-size: 4rem;
}

.project-overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(10, 10, 15, 0.9);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s ease;
}

.project-card:hover .project-overlay {
  opacity: 1;
}

.project-links {
  display: flex;
  gap: 1rem;
}

.project-link {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  background: rgba(255, 255, 255, 0.1);
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  transition: all 0.3s ease;
}

.project-link:hover {
  background: linear-gradient(135deg, #7c3aed, #00d4ff);
  transform: scale(1.1);
}

.project-content {
  padding: 1.5rem;
}

.project-title {
  font-size: 1.3rem;
  font-weight: 600;
  color: #fff;
  margin-bottom: 0.75rem;
}

.project-description {
  color: #a0a0a0;
  font-size: 0.95rem;
  line-height: 1.6;
  margin-bottom: 1.25rem;
}

.project-tags {
  display: flex;
  flex-wrap: wrap;
  gap: 0.5rem;
}

.project-tag {
  padding: 0.35rem 0.75rem;
  background: rgba(124, 58, 237, 0.2);
  border-radius: 20px;
  color: #00d4ff;
  font-size: 0.8rem;
  font-weight: 500;
}
</style>
