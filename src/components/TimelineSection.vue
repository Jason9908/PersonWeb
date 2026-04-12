<template>
  <section id="timeline" class="timeline">
    <h2 class="section-title">人生大事记</h2>
    <p class="section-subtitle">从逆境重生到边学边赚 - 记录人生重要里程碑</p>
    <div class="timeline-container">
      <div
        v-for="(event, index) in timelineEvents"
        :key="index"
        :class="['timeline-item', event.type]"
      >
        <div class="timeline-marker">
          <span class="timeline-icon">{{ event.icon }}</span>
        </div>
        <div class="timeline-content">
          <span class="timeline-year">{{ event.year }}</span>
          <h3 class="timeline-title">{{ event.title }}</h3>
          <p class="timeline-description">{{ event.description }}</p>
        </div>
      </div>
    </div>
    <div class="timeline-quote">
      <p>"我希望人生来过一次，给我多点表达能力，少点记忆"</p>
      <p class="quote-author">— 柯柯</p>
    </div>
  </section>
</template>

<script setup>
const timelineEvents = [
  {
    year: '1999',
    title: '出生',
    description: '8月29日出生于湖南郴州兴宁医院，因脑出血导致二级肢体和智力残疾',
    icon: '👶',
    type: 'milestone'
  },
  {
    year: '2004',
    title: '学会走路',
    description: '5岁从黑暗中醒来，经过治疗终于学会走路',
    icon: '🚶',
    type: 'breakthrough'
  },
  {
    year: '2006',
    title: '入学',
    description: '7岁进入学校，开始真正的学生时代',
    icon: '📚',
    type: 'education'
  },
  {
    year: '2015',
    title: '高中时期',
    description: '在老家县城读普高，遇到一生难忘的人，完成高中学业',
    icon: '🏫',
    type: 'education'
  },
  {
    year: '2018',
    title: '大学',
    description: '进入大学学习物联网应用技术，"只要学不死，就往死里学"',
    icon: '🎓',
    type: 'education'
  },
  {
    year: '2019',
    title: '20万行代码',
    description: '大学期间疯狂学编程，敲了20万行代码，帮同学解决问题',
    icon: '💻',
    type: 'achievement'
  },
  {
    year: '2020',
    title: '疫情在家',
    description: '疫情期间在家上网课，靠着时断时续的手机热点完成学业',
    icon: '🏠',
    type: 'challenge'
  },
  {
    year: '2021',
    title: '毕业找工作',
    description: '到杭州找工作，BOSS聊1000多家，面试100多家，经历多次失败',
    icon: '💼',
    type: 'challenge'
  },
  {
    year: '2021',
    title: '第一单私活',
    description: '数据库试卷5个SQL赚50元，客户给了80元，从0到1打通闭环',
    icon: '💰',
    type: 'achievement'
  },
  {
    year: '2021',
    title: '边学边赚',
    description: 'C++线程25分钟赚200元，Flask项目换显示屏，学生成绩管理系统800元',
    icon: '🎯',
    type: 'achievement'
  },
  {
    year: '2024',
    title: '自媒体之路',
    description: '加入胜哥微天使，开始做IP，5个月私域从0到1100',
    icon: '📱',
    type: 'achievement'
  },
  {
    year: '2025',
    title: 'AI新方向',
    description: '获得香橙派 AI Pro，学习Cursor，50分钟完成聊天室项目赚175元',
    icon: '🤖',
    type: 'achievement'
  },
  {
    year: '2026',
    title: '网站升级',
    description: '个人网站全面升级，添加更多功能和内容，提升用户体验',
    icon: '🌐',
    type: 'achievement'
  }
]
</script>

<style scoped>
.timeline {
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

.timeline-container {
  position: relative;
  max-width: 1000px;
  margin: 3rem auto 0;
  padding: 0 20px;
}

.timeline-container::before {
  content: '';
  position: absolute;
  left: 30px;
  top: 0;
  bottom: 0;
  width: 3px;
  background: linear-gradient(180deg,
    var(--primary-color) 0%,
    var(--secondary-color) 50%,
    var(--accent-color) 100%
  );
  box-shadow: var(--glow);
}

.timeline-item {
  position: relative;
  padding-left: 80px;
  margin-bottom: 3rem;
}

.timeline-marker {
  position: absolute;
  left: 0;
  top: 0;
  width: 60px;
  height: 60px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 1;
  transition: all 0.3s ease;
}

.timeline-item.milestone .timeline-marker {
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  box-shadow: 0 0 20px rgba(0, 240, 255, 0.5);
  border: 3px solid rgba(0, 240, 255, 0.3);
}

.timeline-item.breakthrough .timeline-marker {
  background: linear-gradient(135deg, var(--accent-color), #34d399);
  box-shadow: 0 0 20px rgba(0, 255, 136, 0.5);
  border: 3px solid rgba(0, 255, 136, 0.3);
}

.timeline-item.education .timeline-marker {
  background: linear-gradient(135deg, var(--secondary-color), #9333ea);
  box-shadow: 0 0 20px rgba(123, 44, 191, 0.5);
  border: 3px solid rgba(123, 44, 191, 0.3);
}

.timeline-item.achievement .timeline-marker {
  background: linear-gradient(135deg, #f59e0b, #ef4444);
  box-shadow: 0 0 20px rgba(245, 158, 11, 0.5);
  border: 3px solid rgba(245, 158, 11, 0.3);
}

.timeline-item.challenge .timeline-marker {
  background: linear-gradient(135deg, #6b7280, #374151);
  box-shadow: 0 0 20px rgba(107, 114, 128, 0.3);
  border: 3px solid rgba(107, 114, 128, 0.3);
}

.timeline-icon {
  font-size: 1.8rem;
}

.timeline-item:hover .timeline-marker {
  transform: scale(1.1);
}

.timeline-content {
  background: linear-gradient(135deg, var(--bg-card) 0%, rgba(18, 24, 41, 0.6) 100%);
  padding: 1.5rem;
  border-radius: 16px;
  border: 1px solid rgba(0, 240, 255, 0.1);
  transition: all 0.3s ease;
  position: relative;
}

.timeline-content::before {
  content: '';
  position: absolute;
  left: -10px;
  top: 20px;
  width: 0;
  height: 0;
  border-top: 10px solid transparent;
  border-bottom: 10px solid transparent;
  border-right: 10px solid var(--bg-card);
}

.timeline-item:hover .timeline-content {
  transform: translateX(8px);
  box-shadow: var(--shadow-lg);
  border-color: rgba(0, 240, 255, 0.3);
}

.timeline-year {
  display: inline-block;
  padding: 0.25rem 0.75rem;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  color: var(--bg-darker);
  border-radius: 20px;
  font-size: 0.85rem;
  font-weight: 600;
  margin-bottom: 0.75rem;
  box-shadow: 0 0 15px rgba(0, 240, 255, 0.3);
}

.timeline-title {
  font-size: 1.25rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  color: var(--text-dark);
}

.timeline-description {
  color: var(--text-light);
  line-height: 1.7;
}

.timeline-quote {
  max-width: 700px;
  margin: 4rem auto 0;
  padding: 2rem;
  background: linear-gradient(135deg, rgba(0, 240, 255, 0.1), rgba(123, 44, 191, 0.1));
  border-radius: 16px;
  text-align: center;
  color: white;
  border: 1px solid rgba(0, 240, 255, 0.2);
  box-shadow: var(--shadow);
}

.timeline-quote p {
  font-size: 1.2rem;
  line-height: 1.8;
  margin-bottom: 0.5rem;
}

.quote-author {
  font-size: 1rem;
  opacity: 0.9;
  font-style: italic;
  color: var(--primary-color);
}

@media (max-width: 768px) {
  .timeline-container::before {
    left: 20px;
  }

  .timeline-item {
    padding-left: 60px;
  }

  .timeline-marker {
    width: 40px;
    height: 40px;
  }

  .timeline-icon {
    font-size: 1.2rem;
  }

  .timeline-content {
    padding: 1.25rem;
  }

  .timeline-content::before {
    left: -8px;
    border-width: 8px;
  }
}
</style>
