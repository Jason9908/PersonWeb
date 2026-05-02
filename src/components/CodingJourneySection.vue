<template>
  <section id="coding-journey" class="coding-journey">
    <!-- 背景cmatrix单行滚动效果 -->
    <div class="cmatrix-container">
      <div class="cmatrix-line">
        <span v-for="i in 200" :key="i" class="cmatrix-char">{{ getRandomChar() }}</span>
      </div>
    </div>

    <!-- 鼠标光晕跟随 -->
    <div class="cursor-glow" ref="cursorGlow"></div>

    <!-- 扫描线效果 -->
    <div class="scan-line"></div>
    
    <!-- 加载指示器 -->
    <div v-if="isLoading" class="loading-overlay">
      <div class="loading-content">
        <div class="loading-spinner"></div>
        <div class="loading-progress">
          <div class="loading-progress-bar" :style="{ width: loadingProgress + '%' }"></div>
        </div>
        <div class="loading-text">加载中... {{ loadingProgress }}%</div>
      </div>
    </div>
    
    <h2 class="section-title animate-fade-in">我的编程来时路</h2>
    <h2 class="section-subtitle animate-fade-in">技术学习之路 - 从2009年初识电脑到2025年AI编程</h2>

    <!-- 开篇 -->
    <div class="journey-intro animate-fade-in">
      <p class="intro-text">
        说起我这条路，真是一言难尽。小时候身体不太好，从郴州到广州求医，在老家、资兴、九江到处读书。
        但这些没把我困住，反而让我更想看看外面的世界。学生时代，同学们叫我"得宝"，大概是因为我总是
        笑呵呵的，哪怕在讲台边吃粉笔灰也无所谓。爷爷和叔叔走了，心里难受；暗恋过人，也没结果。
        高中那会儿，老师说我课上厉害、考试拉胯，哈哈。高考后，我一咬牙，选了编程这条路。
      </p>
      <p class="intro-text">
        大学算是真正入门了。C语言、Java，我越学越上头，代码敲了几十万行，证书考了好几个，
        同学有问题都来找我。毕业后找工作可太坎坷了，杭州、深圳跑了一圈，简历投了上千份，
        面试碰壁无数次。穷的时候一天就吃泡面，接到第一单私活赚了钱那个高兴啊。
        但这些挫折没让我放弃，反而让我更清楚自己就是喜欢写代码。
      </p>
    </div>

    <!-- 时间线 -->
    <div class="journey-timeline" ref="timelineRef">
      <!-- 2009年暑假 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">2009年暑假 - 第一次碰电脑</h3>
          <p class="journey-text">
            去阿姨家玩，生平第一次用电脑。啥都不懂，关机直接按电源键，就玩7k7k、4399小游戏。
            那时候哪知道以后会跟这玩意儿打这么多年交道啊。
          </p>
        </div>
      </div>

      <!-- 高三冬日修电脑 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">高三冬日 - 瞎按修好电脑</h3>
          <p class="journey-text">
            一个星期三的中午，我闲得没事干，电脑突然坏了。抱着试试看的心态拆开机箱，
            就按了按里面的内存条什么的，没想到屏幕居然亮起来了！虽然只是瞎按，
            但那一刻心里涌起一股巨大的自豪感，感觉自己什么都能搞定。下午老师上课时，
            看到电脑修好了，说"这电脑能修好，真是牛"。
          </p>
        </div>
      </div>

      <!-- 2018年高考 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">2018年高考 - 选了物联网</h3>
          <p class="journey-text">
            高考完因为喜欢研究东西，选了物联网应用技术。结果发现是嵌入式方向，
            不过也无所谓了，反正跟技术有关就行。
          </p>
        </div>
      </div>

      <!-- Office课程 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">Office课程</h3>
          <p class="journey-text">
            Office课太简单了，计算机基础初中就懂，Office操作虽然没练过但也都会。
            轻松混过去。
          </p>
        </div>
      </div>

      <!-- 单片机课救场 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">单片机课 - 一分钟搞定Proteus</h3>
          <p class="journey-text">
            单片机课上，有的同学只有一个C盘，需要破解Proteus软件。老师折腾半天搞不定，
            就请我帮忙。我上去一分钟就搞定了，老师当场说"牛"。那时候感觉自己有点东西了。
          </p>
        </div>
      </div>

      <!-- C语言课 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">C语言课 - 发誓要学好</h3>
          <p class="journey-text">
            余纯淳老师的C语言课，我暗下决心一定要学会。那一个月看书看懵了，
            还是上手敲代码实在。这门课算是我的编程起点吧。
          </p>
        </div>
      </div>

      <!-- 10月3日买电脑 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">10月3日 - 终于有自己电脑了</h3>
          <p class="journey-text">
            妈妈带着弟弟妹妹和我去县里看电脑，第二天终于买下来了，高兴坏了。
            有了自己的电脑，随时随地都能敲代码，爽。
          </p>
        </div>
      </div>

      <!-- 疯狂敲代码 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">疯狂敲代码</h3>
          <p class="journey-text">
            回到学校就开始疯狂敲C语言，真的是敲到吐。到现在差不多敲了20万行吧，
            不过还是没人要我，哈哈。
          </p>
        </div>
      </div>

      <!-- PowerPoint -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">12月28日 - 做PPT做傻了</h3>
          <p class="journey-text">
            晚上做PowerPoint，做到手指头都僵硬得动不了。是真的拼。
          </p>
        </div>
      </div>

      <!-- 评教表 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">评教表和投票</h3>
          <p class="journey-text">
            班导看我老实，让我填评教表，一填就填了四五个学期。班上投票什么的，
            我因为避嫌从来没给自己投过。
          </p>
        </div>
      </div>

      <!-- 二级Office考试 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">考二级Office</h3>
          <p class="journey-text">
            问老师能不能报二级，顺便加了QQ。第二天考一级，超简单。
            第三天C语言实训，我和鸡仔一下午就搞定了，两个版本救了全班60个人。
            想下周不去机房还不行，哈哈。
          </p>
        </div>
      </div>

      <!-- 刷题考证 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">刷题备考</h3>
          <p class="journey-text">
            在学校疯狂刷题，刷到3月29日。那天晚上睡得早，第二天5:45就起了，
            大学第一次起这么早。和刘汉文坐最早一班车去萍乡总校区考二级Office。
            总校区在村里，考了70分钟就出来了，题都刷过，简单。
          </p>
        </div>
      </div>

      <!-- C语言竞赛 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">5月 - C语言竞赛</h3>
          <p class="journey-text">
            学校搞C语言竞赛，要是我们班抱团肯定能拿第一第二，结果只拿了第四。
            不过我是物联网专业第一，也算不错吧。
          </p>
        </div>
      </div>

      <!-- 通讯录项目 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">端午 - 通讯录项目</h3>
          <p class="journey-text">
            端午回学校开始实训周，周日晚上把函数前七题写完了。第二天下午二分法卡住了，
            找我哥求助。他说"写C语言不用指针就是笑话"，挺有道理的。
            晚上我们五个分任务：我写指针，鸡仔写结构体，其他三个写通讯录。
            第三天上午我的模块搞完了，没事干就自己写通讯录。第一次写这么大的项目，
            以前都是小Demo。遇到不少坑，比如字符型变量要用%s接收。
            下午4点左右写完了，第一版太烂，一直改到周四晚上，干脆用指针重构了一遍。
            这个项目算是我的一个里程碑吧。
          </p>
        </div>
      </div>

      <!-- 达内课程 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">达内课程</h3>
          <p class="journey-text">
            暑假参加了达内的课程，学Java。第一次接触面向对象，有点懵。
            不过跟着敲代码，慢慢就懂了。那段时间进步挺大的。
          </p>
        </div>
      </div>

      <!-- 第一次接单 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">第一次接单</h3>
          <p class="journey-text">
            在淘宝上接了第一个私活，帮人写一个Java小程序。
            虽然钱不多，但那种靠技术赚钱的感觉真爽。
          </p>
        </div>
      </div>

      <!-- 秋招碰壁 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">秋招 - 四处碰壁</h3>
          <p class="journey-text">
            秋招开始投简历，杭州、深圳跑了一圈，投了上千份简历，面试无数次，
            基本都石沉大海。那段时间真的很焦虑，怀疑自己是不是选错行了。
          </p>
        </div>
      </div>

      <!-- 坚持学习 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">坚持学习</h3>
          <p class="journey-text">
            虽然找工作不顺，但还是每天坚持学习。刷LeetCode，看技术博客，
            写开源项目。相信机会总会来的。
          </p>
        </div>
      </div>

      <!-- CSDN博主 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">CSDN博主 - 8K粉</h3>
          <p class="journey-text">
            开始在CSDN写博客，分享技术心得。没想到慢慢有了8000多个粉丝，
            还成了全栈领域新星博主。这给了我很大的信心。
          </p>
        </div>
      </div>

      <!-- 阿里云专家 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">阿里云专家认证</h3>
          <p class="journey-text">
            考了阿里云专家认证，算是对自己技术的一种认可吧。
            继续加油！
          </p>
        </div>
      </div>

      <!-- AI编程 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">2025年 - AI编程</h3>
          <p class="journey-text">
            现在开始学习AI相关的编程，感觉又是一个新的起点。
            技术这条路，学无止境啊。
          </p>
        </div>
      </div>
    </div>

    <!-- 统计数据 -->
    <div class="journey-stats">
      <div class="stat-item animate-on-scroll stat-card">
        <div class="stat-number" data-target="200000">0</div>
        <div class="stat-label">代码行数</div>
      </div>
      <div class="stat-item animate-on-scroll stat-card">
        <div class="stat-number" data-target="8000">0</div>
        <div class="stat-label">CSDN粉丝</div>
      </div>
      <div class="stat-item animate-on-scroll stat-card">
        <div class="stat-number" data-target="4">0</div>
        <div class="stat-label">考的证书</div>
      </div>
      <div class="stat-item animate-on-scroll stat-card">
        <div class="stat-number">∞</div>
        <div class="stat-label">还在学</div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from 'vue'

const cursorGlow = ref(null)
const isLoading = ref(true)
const loadingProgress = ref(0)

const getRandomChar = () => {
  const chars = '0123456789ABCDEFﾊﾋﾌﾍﾎﾏﾐﾑﾒﾓﾔﾕﾖﾗﾘﾙﾚﾛﾜﾝ'
  return chars[Math.floor(Math.random() * chars.length)]
}

const handleMouseMove = (e) => {
  if (cursorGlow.value) {
    const x = e.clientX
    const y = e.clientY
    cursorGlow.value.style.left = `${x}px`
    cursorGlow.value.style.top = `${y}px`
  }
}

const preloadImages = async (images, batchSize = 5) => {
  const imageEntries = Object.entries(images)
  const total = imageEntries.length
  let loaded = 0

  const loadImage = (src, name) => {
    return new Promise((resolve) => {
      const img = new Image()
      img.crossOrigin = 'anonymous'
      img.onload = () => {
        resolve({ name, src, success: true })
      }
      img.onerror = () => {
        resolve({ name, src, success: false })
      }
      img.src = src
    })
  }

  for (let i = 0; i < total; i += batchSize) {
    const batch = imageEntries.slice(i, i + batchSize)
    const batchPromises = batch.map(([name, src]) => loadImage(src, name))
    await Promise.all(batchPromises)
    loaded += batch.length
    loadingProgress.value = Math.round((loaded / total) * 100)
  }

  return true
}

onMounted(async () => {
  try {
    await preloadImages(imagePaths)
  } catch (error) {
    console.error('图片加载失败:', error)
  } finally {
    isLoading.value = false
  }

  document.addEventListener('mousemove', handleMouseMove)

  const observerOptions = {
    root: null,
    rootMargin: '0px',
    threshold: 0.15
  }

  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, index) => {
      if (entry.isIntersecting) {
        setTimeout(() => {
          entry.target.classList.add('is-visible')

          const numberElement = entry.target.querySelector('.stat-number[data-target]')
          if (numberElement) {
            const target = parseInt(numberElement.dataset.target)
            animateNumber(numberElement, target)
          }
        }, index * 100)

        observer.unobserve(entry.target)
      }
    })
  }, observerOptions)

  const animatedElements = document.querySelectorAll('.animate-on-scroll')
  animatedElements.forEach(el => observer.observe(el))

  const fadeElements = document.querySelectorAll('.animate-fade-in')
  fadeElements.forEach((el, index) => {
    setTimeout(() => {
      el.classList.add('is-visible')
    }, index * 200)
  })
})

const imagePaths = {
  airplane: '/PersonWeb/airplane.png',
  xiaobot: '/PersonWeb/xiaobot.png',
  cpp: '/PersonWeb/CPP.png',
  csdn: '/PersonWeb/CSDN.png',
  csdnArticle: '/PersonWeb/CSDNarticle.png',
  score: '/PersonWeb/score.png',
  honor: '/PersonWeb/honor.png',
  screen: '/PersonWeb/screen.png',
  certificate: '/PersonWeb/certificate.png',
  kilo: '/PersonWeb/kilo.png',
  orangePIAIPro: '/PersonWeb/orangePIAIPro.png'
}

const animateNumber = (element, target, duration = 2000) => {
  const start = 0
  const startTime = performance.now()

  const updateNumber = (currentTime) => {
    const elapsed = currentTime - startTime
    const progress = Math.min(elapsed / duration, 1)

    const easeOut = 1 - Math.pow(1 - progress, 4)
    const current = Math.floor(start + (target - start) * easeOut)

    if (target >= 10000) {
      element.textContent = (current / 10000).toFixed(0) + '万+'
    } else if (target >= 1000) {
      element.textContent = (current / 1000).toFixed(0) + 'K+'
    } else {
      element.textContent = current + '+'
    }

    if (progress < 1) {
      requestAnimationFrame(updateNumber)
    }
  }

  requestAnimationFrame(updateNumber)
}
</script>

<style scoped>
.coding-journey {
  min-height: 100vh;
  padding: 80px 20px;
  position: relative;
  overflow: hidden;
}

.cmatrix-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  overflow: hidden;
  pointer-events: none;
  z-index: 0;
}

.cmatrix-line {
  display: flex;
  animation: cmatrixScroll 30s linear infinite;
}

@keyframes cmatrixScroll {
  0% {
    transform: translateX(-100%);
  }
  100% {
    transform: translateX(100%);
  }
}

.cmatrix-char {
  font-family: 'Courier New', monospace;
  font-size: 14px;
  color: rgba(99, 102, 241, 0.6);
  margin: 0 1px;
  animation: cmatrixFlicker 0.5s ease-in-out infinite alternate;
}

@keyframes cmatrixFlicker {
  0% { opacity: 0.5; }
  100% { opacity: 1; }
}

.cursor-glow {
  position: fixed;
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, rgba(99, 102, 241, 0.15), transparent 70%);
  border-radius: 50%;
  pointer-events: none;
  transform: translate(-50%, -50%);
  z-index: 9999;
  transition: opacity 0.3s ease;
  animation: cursorPulse 2s ease-in-out infinite;
}

@keyframes cursorPulse {
  0%, 100% {
    opacity: 0.5;
    transform: translate(-50%, -50%) scale(1);
  }
  50% {
    opacity: 0.8;
    transform: translate(-50%, -50%) scale(1.1);
  }
}

.scan-line {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, transparent, rgba(99, 102, 241, 0.5), transparent);
  animation: scanMove 8s linear infinite;
  z-index: 2;
  pointer-events: none;
}

@keyframes scanMove {
  0% { top: 0; opacity: 0; }
  10% { opacity: 1; }
  90% { opacity: 1; }
  100% { top: 100%; opacity: 0; }
}

.coding-journey::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image:
    linear-gradient(rgba(99, 102, 241, 0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(99, 102, 241, 0.03) 1px, transparent 1px);
  background-size: 50px 50px;
  animation: gridMove 20s linear infinite;
  pointer-events: none;
  z-index: 0;
}

@keyframes gridMove {
  0% { transform: translate(0, 0); }
  100% { transform: translate(50px, 50px); }
}

.loading-overlay {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(5, 8, 22, 0.95);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 9999;
  backdrop-filter: blur(10px);
}

.loading-content {
  text-align: center;
  max-width: 300px;
  padding: 2rem;
  background: linear-gradient(135deg, var(--bg-card) 0%, rgba(18, 24, 41, 0.8) 100%);
  border-radius: 16px;
  border: 1px solid rgba(99, 102, 241, 0.2);
  box-shadow: 0 0 30px rgba(99, 102, 241, 0.3);
}

.loading-spinner {
  width: 60px;
  height: 60px;
  border: 3px solid rgba(99, 102, 241, 0.2);
  border-top: 3px solid var(--primary-color);
  border-radius: 50%;
  animation: spin 1s linear infinite;
  margin: 0 auto 1.5rem;
  box-shadow: 0 0 20px rgba(99, 102, 241, 0.5);
}

@keyframes spin {
  0% { transform: rotate(0deg); }
  100% { transform: rotate(360deg); }
}

.loading-progress {
  width: 100%;
  height: 8px;
  background-color: rgba(99, 102, 241, 0.1);
  border-radius: 4px;
  overflow: hidden;
  margin-bottom: 1rem;
}

.loading-progress-bar {
  height: 100%;
  background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
  border-radius: 4px;
  transition: width 0.3s ease;
  box-shadow: 0 0 10px rgba(99, 102, 241, 0.8);
}

.loading-text {
  color: var(--primary-color);
  font-size: 1.1rem;
  font-weight: 500;
  text-shadow: var(--glow-text);
}

.section-title {
  font-size: 2.5rem;
  font-weight: 700;
  margin-bottom: 1rem;
  color: var(--text-dark);
  text-align: center;
  text-shadow: var(--glow-text);
  letter-spacing: 2px;
  position: relative;
}

.section-title::after {
  content: '';
  position: absolute;
  bottom: -10px;
  left: 50%;
  transform: translateX(-50%);
  width: 0;
  height: 3px;
  background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
  transition: width 1s ease 0.5s;
}

.animate-fade-in.is-visible.section-title::after {
  width: 100px;
}

.section-subtitle {
  font-size: 1.1rem;
  color: var(--text-light);
  text-align: center;
  margin-bottom: 3rem;
  max-width: 100%;
  margin-left: auto;
  margin-right: auto;
  white-space: nowrap;
}

.journey-intro {
  max-width: 900px;
  margin: 0 auto 4rem;
  padding: 2.5rem;
  background: linear-gradient(135deg, var(--bg-card) 0%, rgba(18, 24, 41, 0.6) 100%);
  border-radius: 16px;
  border: 1px solid rgba(99, 102, 241, 0.2);
}

.intro-text {
  color: var(--text-light);
  line-height: 2;
  font-size: 1.05rem;
  text-align: justify;
  margin-bottom: 1.5rem;
  opacity: 0;
  animation: fadeSlideIn 0.8s ease forwards;
}

.intro-text:nth-child(1) { animation-delay: 0.2s; }
.intro-text:nth-child(2) { animation-delay: 0.4s; }

@keyframes fadeSlideIn {
  from { opacity: 0; transform: translateX(-20px); }
  to { opacity: 1; transform: translateX(0); }
}

.intro-text:last-child { margin-bottom: 0; }

.journey-timeline {
  max-width: 1000px;
  margin: 0 auto 4rem;
  position: relative;
}

.journey-timeline::before {
  content: '';
  position: absolute;
  left: 50px;
  top: 0;
  bottom: 0;
  width: 3px;
  background: linear-gradient(180deg, var(--primary-color), var(--secondary-color));
  box-shadow: 0 0 15px rgba(99, 102, 241, 0.5);
}

.journey-item {
  display: flex;
  gap: 2rem;
  margin-bottom: 3rem;
  position: relative;
  padding-left: 30px;
}

.journey-item:nth-child(even) { flex-direction: row-reverse; }

.journey-content {
  flex: 1;
  background: linear-gradient(135deg, var(--bg-card) 0%, rgba(18, 24, 41, 0.6) 100%);
  border-radius: 12px;
  padding: 1.5rem;
  border: 1px solid rgba(99, 102, 241, 0.1);
  transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  position: relative;
  overflow: hidden;
}

.journey-content::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  height: 2px;
  background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.3s ease;
}

.journey-item:hover .journey-content::before { transform: scaleX(1); }

.journey-item:hover .journey-content {
  transform: translateY(-4px);
  box-shadow: 0 0 30px rgba(99, 102, 241, 0.3);
  border-color: rgba(99, 102, 241, 0.3);
}

.journey-title {
  font-size: 1.3rem;
  font-weight: 700;
  margin-bottom: 0.75rem;
  color: var(--primary-color);
  text-shadow: var(--glow-text);
}

.journey-text {
  color: var(--text-light);
  line-height: 1.7;
  font-size: 1rem;
}

.journey-stats {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 1.5rem;
  max-width: 800px;
  margin: 4rem auto 0;
}

.stat-item {
  background: linear-gradient(135deg, var(--bg-card) 0%, rgba(18, 24, 41, 0.6) 100%);
  border-radius: 16px;
  padding: 2rem;
  text-align: center;
  border: 1px solid rgba(99, 102, 241, 0.1);
  transition: all 0.3s ease;
}

.stat-item:hover {
  transform: translateY(-6px);
  box-shadow: var(--shadow-lg);
  border-color: rgba(99, 102, 241, 0.3);
}

.stat-number {
  font-size: 2.5rem;
  font-weight: 800;
  color: var(--primary-color);
  text-shadow: var(--glow-text);
  margin-bottom: 0.5rem;
}

.stat-label {
  font-size: 0.9rem;
  color: var(--text-light);
}

@media (max-width: 768px) {
  .coding-journey { padding: 60px 10px; }

  .section-title { font-size: 1.5rem; }
  .section-subtitle { font-size: 0.9rem; }

  .journey-intro { padding: 1.5rem; }
  .intro-text { font-size: 0.9rem; }

  .journey-timeline::before { left: 25px; }
  .journey-item { padding-left: 15px; gap: 1rem; }
  .journey-content { padding: 1rem; }
  .journey-title { font-size: 1.1rem; }
  .journey-text { font-size: 0.9rem; }

  .journey-stats {
    grid-template-columns: repeat(2, 1fr);
    gap: 1rem;
  }

  .stat-item { padding: 1.5rem; }
  .stat-number { font-size: 1.8rem; }
}

@media (max-width: 360px) {
  .section-title { font-size: 1.2rem; }
  .section-subtitle { font-size: 0.8rem; }

  .journey-stats {
    grid-template-columns: 1fr 1fr;
    gap: 0.5rem;
  }

  .stat-number { font-size: 1.3rem; }
  .stat-label { font-size: 0.7rem; }
}
</style>
