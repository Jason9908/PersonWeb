<template>
  <section id="about" class="about">
    <div class="about-container">
      <div class="about-content">
        <h1 class="about-title">你好，我是柯柯</h1>
        <p class="about-subtitle">庐山人在湖南资兴 | 8K粉技术博主</p>
        <p class="about-description">
          CSDN全栈领域新星博主、阿里云专家、工信部权威认证物联网技术开发工程师。
          热爱分享技术，坚持100天发博客，带你一起边学边赚！
        </p>
        <div class="about-badges">
          <h3>荣誉标签</h3>
          <div class="badges-grid">
            <span class="badge-item">🏆 CSDN全栈领域新星博主</span>
            <span class="badge-item">☁️ 阿里云专家</span>
            <span class="badge-item">📱 物联网技术开发工程师</span>
          </div>
        </div>
        <div class="about-communities">
          <h3>圈子</h3>
          <div class="communities-grid">
            <span class="community-tag">遇见合伙人</span>
            <span class="community-tag">洋洋合伙人</span>
            <span class="community-tag">喜乐合伙人</span>
            <span class="community-tag">小灰风云会</span>
          </div>
        </div>
        <div class="about-skills">
          <h3>技能</h3>
          <div class="skills-grid">
            <span class="skill-tag">C/C++</span>
            <span class="skill-tag">Java</span>
            <span class="skill-tag">Python</span>
            <span class="skill-tag">嵌入式</span>
            <span class="skill-tag">Web开发</span>
            <span class="skill-tag">数据库</span>
          </div>
        </div>
        <ThemeSwitcher />
        <div class="about-actions">
          <a href="#contact" class="btn btn-primary">联系我</a>
          <a href="#achievements" class="btn btn-secondary">了解更多</a>
        </div>
      </div>
      <div class="about-image">
        <img :src="avatarImage" alt="柯柯头像" class="avatar-image" />
      </div>
    </div>
  </section>
</template>

<script setup>
import avatarImage from '../assets/images/avatar.jpg'
import ThemeSwitcher from './ThemeSwitcher.vue'
</script>

<style scoped>
.about {
  background: linear-gradient(135deg, var(--bg-darker) 0%, var(--bg-card) 50%, var(--bg-darker) 100%);
  color: var(--text-dark);
  padding: 100px 0;
  border-bottom: 1px solid rgba(var(--primary-color-rgb), 0.2);
  position: relative;
  overflow: hidden;
}

.about::before {
  content: '';
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: radial-gradient(circle, rgba(var(--primary-color-rgb), 0.1) 0%, transparent 70%);
  animation: rotate 20s linear infinite;
}

@keyframes rotate {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

.about-container {
  max-width: 1000px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
  position: relative;
  z-index: 1;
}

.about-title {
  font-size: 3rem;
  font-weight: 800;
  margin-bottom: 0.5rem;
  line-height: 1.2;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color), var(--accent-color));
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  text-shadow: none;
  letter-spacing: 2px;
}

.about-subtitle {
  font-size: 1.25rem;
  opacity: 0.9;
  margin-bottom: 1.5rem;
  color: var(--primary-color);
  text-shadow: var(--glow-text);
}

.about-description {
  font-size: 1.1rem;
  line-height: 1.8;
  opacity: 0.9;
  margin-bottom: 2rem;
  color: rgba(255, 255, 255, 0.85);
}

.about-badges h3,
.about-communities h3,
.about-skills h3 {
  font-size: 1.1rem;
  margin-bottom: 1rem;
  font-weight: 600;
  color: var(--primary-color);
}

.badges-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
  margin-bottom: 1.5rem;
}

.badge-item {
  background: linear-gradient(135deg, rgba(255, 215, 0, 0.2), rgba(255, 193, 7, 0.3));
  color: #ffd700;
  padding: 0.5rem 1rem;
  border-radius: 20px;
  font-size: 0.9rem;
  font-weight: 600;
  border: 1px solid rgba(255, 215, 0, 0.3);
  box-shadow: 0 0 10px rgba(255, 215, 0, 0.2);
}

.communities-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
  margin-bottom: 1.5rem;
}

.community-tag {
  background-color: rgba(0, 240, 255, 0.1);
  padding: 0.5rem 1rem;
  border-radius: 20px;
  font-size: 0.9rem;
  border: 1px solid rgba(0, 240, 255, 0.3);
  color: var(--primary-color);
}

.skills-grid {
  display: flex;
  flex-wrap: wrap;
  gap: 0.75rem;
  justify-content: center;
}

.skill-tag {
  background-color: rgba(123, 44, 191, 0.2);
  padding: 0.5rem 1rem;
  border-radius: 20px;
  font-size: 0.9rem;
  border: 1px solid rgba(123, 44, 191, 0.4);
  color: #cd93ff;
  font-weight: 600;
  transition: all 0.3s ease;
}

.skill-tag:hover {
  background-color: rgba(123, 44, 191, 0.3);
  box-shadow: 0 0 15px rgba(123, 44, 191, 0.5);
  transform: translateY(-2px);
}

.about-actions {
  display: flex;
  gap: 1rem;
  flex-wrap: wrap;
}

.btn {
  padding: 0.75rem 1.5rem;
  border-radius: 8px;
  font-weight: 600;
  transition: all 0.3s ease;
  display: inline-block;
  letter-spacing: 1px;
}

.btn-primary {
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  color: var(--bg-darker);
  border: none;
  box-shadow: 0 0 20px rgba(0, 240, 255, 0.3);
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 0 30px rgba(0, 240, 255, 0.5);
}

.btn-secondary {
  background-color: transparent;
  color: var(--primary-color);
  border: 2px solid var(--primary-color);
}

.btn-secondary:hover {
  background-color: rgba(0, 240, 255, 0.1);
  box-shadow: 0 0 20px rgba(0, 240, 255, 0.3);
}

.about-image {
  display: flex;
  justify-content: center;
  align-items: center;
}

.avatar-image {
  width: 300px;
  height: 300px;
  border-radius: 50%;
  object-fit: cover;
  border: 4px solid var(--primary-color);
  box-shadow: 0 0 40px rgba(0, 240, 255, 0.4), 0 0 80px rgba(123, 44, 191, 0.2);
  animation: pulse-glow 3s ease-in-out infinite;
}

@keyframes pulse-glow {
  0%, 100% {
    box-shadow: 0 0 40px rgba(0, 240, 255, 0.4), 0 0 80px rgba(123, 44, 191, 0.2);
  }
  50% {
    box-shadow: 0 0 60px rgba(0, 240, 255, 0.6), 0 0 100px rgba(123, 44, 191, 0.3);
  }
}

@media (max-width: 968px) {
  .about {
    padding: 60px 0;
  }

  .about-container {
    grid-template-columns: 1fr;
    gap: 2rem;
    text-align: center;
  }

  .about-title {
    font-size: 2rem;
  }

  .about-actions {
    justify-content: center;
  }

  .avatar-image {
    width: 200px;
    height: 200px;
  }

  .skills-grid {
    justify-content: center;
  }
}
</style>
