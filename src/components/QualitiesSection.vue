<template>
  <section id="qualities" class="personality">
    <h2 class="section-title">我的人格特质</h2>
    <p class="section-subtitle">了解真正的柯柯 - 不只是技术博主，更是一个有故事的人</p>

    <div class="personality-intro">
      <div class="intro-text">
        <h3>我是谁？</h3>
        <p>
          我是郭樟柯，一个1999年出生在湖南郴州的程序员。因为出生时的意外，
          我有了二级肢体残疾和二级智力残疾。但我不甘心被命运定义，
          用"闷骚的野蛮生长"来形容我的人生再合适不过了。
        </p>
        <p>
          我用笑容掩盖内心的痛处，用代码表达无法言说的情感。
          从被人看不起到CSDN 8K粉博主，从接不到私活到边学边赚，
          这一路走来，我证明了：起点不重要，重要的是你是否愿意拼命往上爬。
        </p>
      </div>
    </div>

    <div class="traits-grid">
      <div
        v-for="(trait, index) in traits"
        :key="index"
        class="trait-card"
        :style="{ '--trait-color': trait.color }"
      >
        <div class="trait-icon" :style="{ backgroundColor: trait.color }">
          {{ trait.icon }}
        </div>
        <h3 class="trait-name">{{ trait.name }}</h3>
        <p class="trait-description">{{ trait.description }}</p>
      </div>
    </div>

    <div class="mottoes-section">
      <h3>我的座右铭</h3>
      <div class="mottoes-list">
        <div v-for="(motto, index) in mottoes" :key="index" class="motto-item">
          <span class="motto-quote">"</span>
          <p class="motto-text">{{ motto }}</p>
        </div>
      </div>
    </div>

    <div class="personality-footer">
      <p>
        "我想在编程界打出一片属于自己的天地，虽然现在还是未完成时，但我相信，
        只要继续努力，终会有一天能画出圆满的句号。"
      </p>
    </div>
  </section>
</template>

<script setup>
const traits = [
  {
    name: '顽强不屈',
    icon: '💪',
    description: '从出生有残疾到学会走路，从被人看不起到考上大学',
    color: '#ef4444'
  },
  {
    name: '勤奋好学',
    icon: '📖',
    description: '大学期间敲了20万行代码，只要学不死就往死里学',
    color: '#3b82f6'
  },
  {
    name: '乐于助人',
    icon: '🤝',
    description: '帮同学安装软件200遍，解答无数技术问题，当班级的"救火队员"',
    color: '#10b981'
  },
  {
    name: '边学边赚',
    icon: '💰',
    description: '30分钟C++线程赚200元，Flask项目换显示屏，数据库试卷80元',
    color: '#f59e0b'
  },
  {
    name: '感恩之心',
    icon: '❤️',
    description: '特别感谢父母和家人对我不离不弃，虽然一次又一次内疚',
    color: '#ec4899'
  },
  {
    name: '闷骚外表',
    icon: '🎭',
    description: '别看我平时嘻嘻哈哈，其实是以笑容掩盖心中痛处',
    color: '#8b5cf6'
  },
  {
    name: '行动力强',
    icon: '⚡',
    description: '说干就干，两天手撸EasyX飞机大战，25分钟完成C++线程项目',
    color: '#f97316'
  },
  {
    name: '永不放弃',
    icon: '🔥',
    description: '面试失败多次依然坚持，从0到1打通技术变现闭环',
    color: '#dc2626'
  }
]

const mottoes = [
  '只要学不死，就往死里学',
  '我希望人生来过一次，给我多点表达能力，少点记忆',
  '闷骚的野蛮生长',
  '我想在编程界打出一片属于自己的天地'
]
</script>

<style scoped>
.personality {
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

.personality-intro {
  max-width: 800px;
  margin: 3rem auto 0;
  padding: 2rem;
  background: linear-gradient(135deg, rgba(0, 240, 255, 0.1), rgba(123, 44, 191, 0.1));
  border-radius: 20px;
  color: white;
  border: 1px solid rgba(0, 240, 255, 0.2);
  box-shadow: var(--shadow);
}

.intro-text h3 {
  font-size: 1.8rem;
  margin-bottom: 1rem;
  color: var(--primary-color);
  text-shadow: var(--glow-text);
}

.intro-text p {
  font-size: 1.05rem;
  line-height: 1.8;
  margin-bottom: 1rem;
  opacity: 0.95;
  color: rgba(255, 255, 255, 0.9);
}

.traits-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(280px, 1fr));
  gap: 1.5rem;
  margin-top: 3rem;
  margin-bottom: 3rem;
}

.trait-card {
  background: linear-gradient(135deg, var(--bg-card) 0%, rgba(18, 24, 41, 0.6) 100%);
  border-radius: 16px;
  padding: 2rem;
  text-align: center;
  transition: all 0.3s ease;
  position: relative;
  overflow: hidden;
  border: 1px solid rgba(0, 240, 255, 0.1);
}

.trait-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 4px;
  background: var(--trait-color);
  transform: scaleX(0);
  transition: transform 0.3s ease;
  box-shadow: 0 0 10px var(--trait-color);
}

.trait-card:hover::before {
  transform: scaleX(1);
}

.trait-card:hover {
  transform: translateY(-8px);
  box-shadow: var(--shadow-lg);
  border-color: rgba(0, 240, 255, 0.3);
}

.trait-icon {
  width: 70px;
  height: 70px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  margin: 0 auto 1.5rem;
  font-size: 2rem;
  box-shadow: 0 0 20px var(--trait-color);
  border: 2px solid var(--trait-color);
}

.trait-name {
  font-size: 1.3rem;
  font-weight: 700;
  margin-bottom: 0.75rem;
  color: var(--text-dark);
}

.trait-description {
  color: var(--text-light);
  line-height: 1.7;
  font-size: 0.95rem;
}

.mottoes-section {
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem;
  background: linear-gradient(135deg, var(--bg-card) 0%, rgba(18, 24, 41, 0.6) 100%);
  border-radius: 16px;
  border: 1px solid rgba(0, 240, 255, 0.1);
}

.mottoes-section h3 {
  text-align: center;
  font-size: 1.5rem;
  margin-bottom: 2rem;
  color: var(--text-dark);
  text-shadow: var(--glow-text);
}

.mottoes-list {
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.motto-item {
  display: flex;
  align-items: flex-start;
  gap: 1rem;
  padding: 1rem;
  background: rgba(10, 14, 39, 0.6);
  border-radius: 12px;
  border: 1px solid rgba(0, 240, 255, 0.1);
  transition: all 0.3s ease;
}

.motto-item:hover {
  transform: translateX(8px);
  box-shadow: var(--shadow);
  border-color: var(--primary-color);
}

.motto-quote {
  font-size: 3rem;
  line-height: 1;
  color: var(--primary-color);
  font-weight: bold;
  flex-shrink: 0;
  text-shadow: var(--glow-text);
}

.motto-text {
  font-size: 1.1rem;
  line-height: 1.6;
  color: var(--text-dark);
  font-style: italic;
  padding-top: 0.5rem;
}

.personality-footer {
  max-width: 800px;
  margin: 3rem auto 0;
  padding: 2rem;
  text-align: center;
  border: 2px solid var(--primary-color);
  border-radius: 16px;
  background: linear-gradient(135deg, rgba(0, 240, 255, 0.1), rgba(123, 44, 191, 0.1));
  box-shadow: var(--shadow);
}

.personality-footer p {
  font-size: 1.1rem;
  line-height: 1.8;
  color: var(--text-dark);
}

@media (max-width: 768px) {
  .personality-intro {
    padding: 1.5rem;
  }

  .intro-text h3 {
    font-size: 1.5rem;
  }

  .intro-text p {
    font-size: 1rem;
  }

  .traits-grid {
    grid-template-columns: 1fr;
    gap: 1rem;
  }

  .trait-card {
    padding: 1.5rem;
  }

  .trait-icon {
    width: 60px;
    height: 60px;
    font-size: 1.8rem;
  }

  .mottoes-section {
    padding: 1.5rem;
  }

  .motto-quote {
    font-size: 2rem;
  }

  .motto-text {
    font-size: 1rem;
  }

  .personality-footer {
    padding: 1.5rem;
  }

  .personality-footer p {
    font-size: 1rem;
  }
}
</style>
