<template>
  <section id="home" class="hero">
    <div class="hero-content">
      <div class="hero-text">
        <p class="greeting">你好，我是</p>
        <h1 class="name">
          <span class="gradient-text">柯柯</span>
        </h1>
        <p class="title">CSDN全栈领域新星博主 | 阿里云专家 | 物联网工程师</p>
        <p class="description">
          庐山人在湖南资兴 | 8K粉技术博主 Jasonakeke
          热爱分享，专注技术，边学边赚。
        </p>
        <div class="cta-buttons">
          <a href="#projects" class="btn btn-primary">查看项目</a>
          <a href="#contact" class="btn btn-secondary">联系我</a>
        </div>
      </div>
      <div class="hero-visual">
        <div class="code-block">
          <div class="code-header">
            <span class="dot red"></span>
            <span class="dot yellow"></span>
            <span class="dot green"></span>
          </div>
          <pre class="code-content"><code><span class="keyword">const</span> <span class="variable">keke</span> = {
  <span class="key">name</span>: <span class="string">"柯柯"</span>,
  <span class="key">title</span>: <span class="string">"全栈开发工程师"</span>,
  <span class="key">skills</span>: [<span class="string">"C/C++"</span>, <span class="string">"Java"</span>, <span class="string">"Python"</span>, <span class="string">"Web"</span>],
  <span class="key">achievements</span>: {
    <span class="key">csdn</span>: <span class="string">"8K+ 粉丝博主"</span>,
    <span class="key">cert</span>: <span class="string">"阿里云专家"</span>,
    <span class="key">iot</span>: <span class="string">"物联网工程师认证"</span>
  },
  <span class="key">motto</span>: <span class="string">"边学边赚，持续成长"</span>
};</code></pre>
        </div>
      </div>
    </div>
    <div class="scroll-indicator">
      <div class="mouse">
        <div class="wheel"></div>
      </div>
    </div>
  </section>
</template>

<script setup>
</script>

<style scoped>
.hero {
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 2rem;
  position: relative;
  overflow: hidden;
}

.hero::before {
  content: '';
  position: absolute;
  top: -50%;
  right: -20%;
  width: 600px;
  height: 600px;
  background: radial-gradient(circle, rgba(124, 58, 237, 0.15) 0%, transparent 70%);
  border-radius: 50%;
  filter: blur(60px);
  animation: float 8s ease-in-out infinite;
}

.hero::after {
  content: '';
  position: absolute;
  bottom: -30%;
  left: -10%;
  width: 500px;
  height: 500px;
  background: radial-gradient(circle, rgba(0, 212, 255, 0.1) 0%, transparent 70%);
  border-radius: 50%;
  filter: blur(60px);
  animation: float 10s ease-in-out infinite reverse;
}

@keyframes float {
  0%, 100% { transform: translate(0, 0); }
  50% { transform: translate(30px, -30px); }
}

.hero-content {
  max-width: 1200px;
  width: 100%;
  display: grid;
  grid-template-columns: 1fr 1fr;
  gap: 4rem;
  align-items: center;
  position: relative;
  z-index: 1;
}

.hero-text {
  animation: fadeInUp 1s ease;
}

.greeting {
  color: #7c3aed;
  font-size: 1.1rem;
  font-weight: 500;
  margin-bottom: 0.5rem;
}

.name {
  font-size: 4rem;
  font-weight: 700;
  margin: 0.5rem 0;
  line-height: 1.1;
}

.gradient-text {
  background: linear-gradient(135deg, #fff 0%, #00d4ff 50%, #7c3aed 100%);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
}

.title {
  color: #a0a0a0;
  font-size: 1.3rem;
  margin-bottom: 1.5rem;
}

.description {
  color: #808080;
  font-size: 1.1rem;
  line-height: 1.8;
  margin-bottom: 2.5rem;
  max-width: 500px;
}

.cta-buttons {
  display: flex;
  gap: 1rem;
}

.btn {
  padding: 1rem 2rem;
  border-radius: 8px;
  font-size: 1rem;
  font-weight: 600;
  text-decoration: none;
  transition: all 0.3s ease;
  display: inline-block;
}

.btn-primary {
  background: linear-gradient(135deg, #7c3aed 0%, #00d4ff 100%);
  color: #fff;
  border: none;
}

.btn-primary:hover {
  transform: translateY(-2px);
  box-shadow: 0 10px 30px rgba(124, 58, 237, 0.4);
}

.btn-secondary {
  background: transparent;
  color: #fff;
  border: 2px solid rgba(255, 255, 255, 0.2);
}

.btn-secondary:hover {
  border-color: #7c3aed;
  background: rgba(124, 58, 237, 0.1);
}

.hero-visual {
  display: flex;
  justify-content: center;
  animation: fadeInRight 1s ease 0.2s both;
}

.code-block {
  background: rgba(20, 20, 30, 0.8);
  border-radius: 16px;
  border: 1px solid rgba(255, 255, 255, 0.1);
  overflow: hidden;
  box-shadow: 0 25px 50px rgba(0, 0, 0, 0.5);
  max-width: 450px;
}

.code-header {
  background: rgba(255, 255, 255, 0.05);
  padding: 1rem;
  display: flex;
  gap: 0.5rem;
}

.dot {
  width: 12px;
  height: 12px;
  border-radius: 50%;
}

.dot.red { background: #ff5f57; }
.dot.yellow { background: #ffbd2e; }
.dot.green { background: #28c840; }

.code-content {
  padding: 1.5rem;
  margin: 0;
  color: #d4d4d4;
  font-size: 0.9rem;
  line-height: 1.8;
  overflow-x: auto;
}

.code-content .keyword { color: #c586c0; }
.code-content .variable { color: #9cdcfe; }
.code-content .key { color: #9cdcfe; }
.code-content .string { color: #ce9178; }

.scroll-indicator {
  position: absolute;
  bottom: 2rem;
  left: 50%;
  transform: translateX(-50%);
  animation: bounce 2s infinite;
}

.mouse {
  width: 26px;
  height: 40px;
  border: 2px solid rgba(255, 255, 255, 0.3);
  border-radius: 20px;
  position: relative;
}

.wheel {
  width: 4px;
  height: 8px;
  background: rgba(255, 255, 255, 0.5);
  border-radius: 2px;
  position: absolute;
  top: 8px;
  left: 50%;
  transform: translateX(-50%);
  animation: scroll 2s infinite;
}

@keyframes bounce {
  0%, 20%, 50%, 80%, 100% { transform: translateX(-50%) translateY(0); }
  40% { transform: translateX(-50%) translateY(-10px); }
  60% { transform: translateX(-50%) translateY(-5px); }
}

@keyframes scroll {
  0% { opacity: 1; transform: translateX(-50%) translateY(0); }
  100% { opacity: 0; transform: translateX(-50%) translateY(15px); }
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(30px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes fadeInRight {
  from {
    opacity: 0;
    transform: translateX(30px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@media (max-width: 968px) {
  .hero-content {
    grid-template-columns: 1fr;
    text-align: center;
  }

  .hero-text {
    order: 2;
  }

  .hero-visual {
    order: 1;
  }

  .name {
    font-size: 2.5rem;
  }

  .cta-buttons {
    justify-content: center;
  }

  .description {
    margin-left: auto;
    margin-right: auto;
  }
}
</style>
