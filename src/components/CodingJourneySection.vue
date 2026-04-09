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
    <h2 class="section-title animate-fade-in">我的编程来时路</h2>
    <p class="section-subtitle animate-fade-in">技术学习之路 - 从2009年初识电脑到2025年AI编程</p>

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
            下学期学校跟达内合作，派了几个老师过来。教数据库的亮哥，搞嵌入式的辉哥，
            还有老何教UC。亮哥不教废话，只教有用的，晚上和补课从来不上。
            辉哥老给我们派任务，让我们抢着做，2048我做了好几个版本。
            老何的UC课其实就是Linux C，讲了基本命令、Vim、分文件编程、文件读写和UDP。
            跟着他们我们养成了敲笔记的习惯。
          </p>
        </div>
      </div>

      <!-- 二级C语言考试 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">12月21日 - 考二级C语言</h3>
          <p class="journey-text">
            去总校考二级C，去早了在图书馆看书。考试30分钟就出来了，
            别人还在摸软件，监考老师以为我不会做。哈哈。
          </p>
        </div>
      </div>

      <!-- 工信部证书 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-image">
          <img :src="imagePaths.certificate" alt="考取证书" />
        </div>
        <div class="journey-content">
          <h3 class="journey-title">工信部证书</h3>
          <p class="journey-text">
            说工信部证书就两天的课，我说是闹呢。结果给了8天，还是亮哥教。
            其实这个证是拿Java做项目，我们连Java都没学过。第一天搭环境累死我了，
            中午12:30才回去，吃完饭没休息就去别人那搭环境，害得我去教室前排没座位。
            一个下午亮哥教了我们两个月的东西。幸好我脑子转得快，从此对Java有兴趣了。
            亮哥还给了Java学习大纲和网站，Java开发速度快，确实香。
          </p>
        </div>
      </div>

      <!-- Java项目 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">Java项目</h3>
          <p class="journey-text">
            课程结束要交项目，我一个人做了十几个版本，做得我都快吐了。
            不过做完还挺有成就感的。
          </p>
        </div>
      </div>

      <!-- 电脑转轴坏了 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">12月 - 电脑转轴坏了</h3>
          <p class="journey-text">
            电脑转轴坏了，修了花了500块。心疼啊，不过电脑是吃饭的家伙，没办法。
          </p>
        </div>
      </div>

      <!-- 实训周 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">12月 - 实训周</h3>
          <p class="journey-text">
            数据库实训一天就搞完了，剩下时间写实训报告和两篇论文。UC实训要写聊天功能和文件传输，
            三天半搞定。代码能力确实提高了不少。
          </p>
        </div>
      </div>

      <!-- 2020年疫情 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-content">
          <h3 class="journey-title">2020年 - 疫情在家</h3>
          <p class="journey-text">
            2020年赶上疫情，被困在家里。辉哥一个人扛了Qt、ARM和WSN三门课。
            可惜WSN没有硬件，最后就上了Qt课。3个G的教程包，靠时断时续的手机热点
            下了三个小时，下完就发到班级群了。疫情也没耽误学习。
          </p>
        </div>
      </div>

      <!-- 2019年两天手撸飞机大战 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-image">
          <img :src="imagePaths.airplane" alt="飞机大战" />
        </div>
        <div class="journey-content">
          <h3 class="journey-title">2019年 - 两天写个飞机大战</h3>
          <p class="journey-text">
            花了两天时间，从头写了个飞机大战游戏。没抄代码，没套框架，
            自己瞎琢磨出来的。能跑起来还挺有成就感的。
          </p>
        </div>
      </div>

      <!-- 大学分数 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-image">
          <img :src="imagePaths.score" alt="大学成绩" />
        </div>
        <div class="journey-content">
          <h3 class="journey-title">大学成绩</h3>
          <p class="journey-text">
            在校成绩还行，专业课基本都在前面。奖学金差一点没拿到，不过也无所谓了。
            同学觉得我是学霸，老师也还认可我。
          </p>
        </div>
      </div>

      <!-- 2021年半年面试杭州深圳无果 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-image">
          <img :src="imagePaths.kilo" alt="求职之路" />
        </div>
        <div class="journey-content">
          <h3 class="journey-title">2021年 - 找工作撞墙半年</h3>
          <p class="journey-text">
            毕业找工作太难了。杭州深圳跑了一圈，简历投了上千份，面试无数次，
            就是找不到工作。那半年真是低谷，穷到吃泡面，不过没想过放弃编程。
          </p>
        </div>
      </div>

      <!-- 2022年写CSDN博文 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-image">
          <img :src="imagePaths.csdn" alt="CSDN博主" />
        </div>
        <div class="journey-content">
          <h3 class="journey-title">2022年 - 开始写博客</h3>
          <p class="journey-text">
            在CSDN上开始写技术博客，分享学习心得和项目经验。
            坚持写了一阵子，粉丝慢慢涨起来了，还成了全栈领域的新星博主。
            虽然粉丝不算多，但也挺高兴的。
          </p>
        </div>
      </div>

      <!-- 2022年写CSDN博文 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-image">
          <img :src="imagePaths.csdnArticle" alt="CSDN文章" />
        </div>
        <div class="journey-content">
          <h3 class="journey-title">2022年 - 写技术文章</h3>
          <p class="journey-text">
            坚持写文章，内容有嵌入式、Web开发、编程心得这些。
            能帮到一些初学者也挺开心的，读者反馈也还不错。
          </p>
        </div>
      </div>

      <!-- 2022年靠接私活添置屏幕 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-image">
          <img :src="imagePaths.screen" alt="新屏幕" />
        </div>
        <div class="journey-content">
          <h3 class="journey-title">2022年 - 接私活买屏幕</h3>
          <p class="journey-text">
            工作找不到，开始接私活维持生计。靠技术做了几个项目，
            用赚的钱买了块新屏幕。拿到屏幕那一刻，觉得自己走这条路还是对的。
          </p>
        </div>
      </div>

      <!-- 半个小时手撸C++线程200元 -->
      <div class="journey-item animate-on-scroll cpp-special">
        <div class="journey-image cpp-image-wrapper">
          <div class="code-rain"></div>
          <div class="code-rain"></div>
          <div class="code-rain"></div>
          <img :src="imagePaths.cpp" alt="C++多线程" class="cpp-glow" />
          <div class="typing-effect">&lt;thread&gt;</div>
        </div>
        <div class="journey-content">
          <h3 class="journey-title">半小时C++多线程 - 赚了200</h3>
          <p class="journey-text">
            有人让我帮忙写个C++多线程程序，半小时搞定，赚了200块。
            这时候才明白技术真的能变现，接单这条路能走。
          </p>
        </div>
      </div>

      <!-- 2023年与人合作小报童 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-image">
          <img :src="imagePaths.xiaobot" alt="小报童" />
        </div>
        <div class="journey-content">
          <h3 class="journey-title">2023年 - 搞小报童</h3>
          <p class="journey-text">
            跟人合作开始做知识付费，小报童这些平台都试了试。
            把自己的经验整理成付费内容，帮别人学习，自己也能赚点钱。
            一举两得吧。
          </p>
        </div>
      </div>

      <!-- 2024年写一篇博文换开发板 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-image">
          <img :src="imagePaths.orangePIAIPro" alt="Orange Pi AI Pro" />
        </div>
        <div class="journey-content">
          <h3 class="journey-title">2024年 - 写博文换开发板</h3>
          <p class="journey-text">
            写了篇Orange Pi AI Pro的博文，官方认可了，送了我一块开发板。
            技术分享这条路走对了，还接触到了AI嵌入式的新技术。
            挺爽的。
          </p>
        </div>
      </div>

      <!-- 2025年AI编程志愿者 -->
      <div class="journey-item animate-on-scroll">
        <div class="journey-image">
          <img :src="imagePaths.honor" alt="AI编程志愿者" />
        </div>
        <div class="journey-content">
          <h3 class="journey-title">2025年 - AI编程志愿者</h3>
          <p class="journey-text">
            当了AI编程志愿者，帮更多人学AI编程。AI时代来了，
            不学不行啊。边学边分享，能帮到别人也挺有意义的。
          </p>
        </div>
      </div>
    </div>

    <!-- 统计数据 -->
    <div class="journey-stats" ref="statsRef">
      <div class="stat-item animate-on-scroll stat-card">
        <div class="stat-number" data-target="200000">0</div>
        <div class="stat-label">敲过代码</div>
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

// 生成cmatrix列样式
const cmatrixColumnStyle = (index) => {
  return {
    left: `${(index / 40) * 100}%`,
    animationDelay: `${Math.random() * 5}s`,
    animationDuration: `${3 + Math.random() * 4}s`
  }
}

// 生成随机字符
const getRandomChar = () => {
  const chars = '0123456789ABCDEFﾊﾋﾌﾍﾎﾏﾐﾑﾒﾓﾔﾕﾖﾗﾘﾙﾚﾛﾜﾝ'
  return chars[Math.floor(Math.random() * chars.length)]
}

// 鼠标移动跟随效果
const handleMouseMove = (e) => {
  if (cursorGlow.value) {
    const x = e.clientX
    const y = e.clientY
    cursorGlow.value.style.left = `${x}px`
    cursorGlow.value.style.top = `${y}px`
  }
}

// 添加事件监听
onMounted(() => {
  // 鼠标跟随事件
  document.addEventListener('mousemove', handleMouseMove)

  const observerOptions = {
    root: null,
    rootMargin: '0px',
    threshold: 0.15
  }

  const observer = new IntersectionObserver((entries) => {
    entries.forEach((entry, index) => {
      if (entry.isIntersecting) {
        // 添加延迟动画效果
        setTimeout(() => {
          entry.target.classList.add('is-visible')

          // 如果是统计数字，触发计数动画
          const numberElement = entry.target.querySelector('.stat-number[data-target]')
          if (numberElement) {
            const target = parseInt(numberElement.dataset.target)
            animateNumber(numberElement, target)
          }
        }, index * 100) // 每个元素延迟100ms

        observer.unobserve(entry.target)
      }
    })
  }, observerOptions)

  // 观察所有需要动画的元素
  const animatedElements = document.querySelectorAll('.animate-on-scroll')
  animatedElements.forEach(el => observer.observe(el))

  // 观察淡入元素
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

// 数字计数动画
const animateNumber = (element, target, duration = 2000) => {
  const start = 0
  const startTime = performance.now()

  const updateNumber = (currentTime) => {
    const elapsed = currentTime - startTime
    const progress = Math.min(elapsed / duration, 1)

    // 使用 easeOutQuart 缓动函数
    const easeOut = 1 - Math.pow(1 - progress, 4)
    const current = Math.floor(start + (target - start) * easeOut)

    if (target >= 10000) {
      element.textContent = (current / 10000).toFixed(0) + '万+'
    } else if (target >= 1000) {
      element.textContent = (current / 1000).toFixed(0) + 'K+'
    } else {
      element.textContent = current
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
  background-color: var(--bg-darker);
  padding: 80px 20px;
  overflow: hidden;
  position: relative;
}

/* cmatrix单行滚动效果 */
.cmatrix-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  pointer-events: none;
  overflow: hidden;
  z-index: 1;
  opacity: 0.12;
}

.cmatrix-line {
  position: absolute;
  top: 50%;
  left: 0;
  width: 200%;
  display: flex;
  white-space: nowrap;
  font-family: 'Courier New', monospace;
  font-size: 16px;
  font-weight: bold;
  color: #0f0;
  text-shadow: 0 0 10px #0f0;
  animation: cmatrixScroll 20s linear infinite;
  transform: translateY(-50%);
}

@keyframes cmatrixScroll {
  0% {
    transform: translateX(0) translateY(-50%);
  }
  100% {
    transform: translateX(-50%) translateY(-50%);
  }
}

.cmatrix-char {
  display: inline-block;
  width: 20px;
  text-align: center;
  animation: cmatrixBlink 0.5s ease-in-out infinite alternate;
}

@keyframes cmatrixBlink {
  0% {
    opacity: 0.3;
    text-shadow: 0 0 5px #0f0;
  }
  100% {
    opacity: 1;
    text-shadow: 0 0 15px #0f0, 0 0 25px #0f0;
  }
}

/* 鼠标光晕跟随 */
.cursor-glow {
  position: fixed;
  width: 300px;
  height: 300px;
  background: radial-gradient(circle, rgba(0, 240, 255, 0.15), transparent 70%);
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

/* 扫描线效果 */
.scan-line {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 2px;
  background: linear-gradient(90deg, transparent, rgba(0, 240, 255, 0.5), transparent);
  animation: scanMove 8s linear infinite;
  z-index: 2;
  pointer-events: none;
}

@keyframes scanMove {
  0% {
    top: 0;
    opacity: 0;
  }
  10% {
    opacity: 1;
  }
  90% {
    opacity: 1;
  }
  100% {
    top: 100%;
    opacity: 0;
  }
}

/* 背景网格动画 */
.coding-journey::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-image:
    linear-gradient(rgba(0, 240, 255, 0.03) 1px, transparent 1px),
    linear-gradient(90deg, rgba(0, 240, 255, 0.03) 1px, transparent 1px);
  background-size: 50px 50px;
  animation: gridMove 20s linear infinite;
  pointer-events: none;
  z-index: 0;
}

@keyframes gridMove {
  0% {
    transform: translate(0, 0);
  }
  100% {
    transform: translate(50px, 50px);
  }
}

/* 时间线发光增强 */
.journey-timeline::before {
  animation: timelineGlow 3s ease-in-out infinite alternate, glowLine 3s ease-in-out infinite alternate;
}

@keyframes timelineGlow {
  0% {
    filter: brightness(1) drop-shadow(0 0 5px rgba(0, 240, 255, 0.5));
  }
  100% {
    filter: brightness(1.3) drop-shadow(0 0 15px rgba(0, 240, 255, 0.8));
  }
}

/* 全局悬浮效果 */
.journey-item {
  transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
}

.journey-item:hover {
  z-index: 10;
}

/* 标题打字机效果 */
.section-title {
  position: relative;
  overflow: hidden;
}

.section-title::after {
  content: '';
  position: absolute;
  bottom: -10px;
  left: 0;
  width: 0;
  height: 3px;
  background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
  animation: titleUnderline 1s ease forwards 0.5s;
}

@keyframes titleUnderline {
  to {
    width: 100px;
  }
}

/* 开篇卡片发光 */
.journey-intro {
  position: relative;
  z-index: 3;
  animation: introGlow 4s ease-in-out infinite alternate;
}

@keyframes introGlow {
  0% {
    box-shadow: 0 0 20px rgba(0, 240, 255, 0.1);
  }
  100% {
    box-shadow: 0 0 40px rgba(0, 240, 255, 0.3);
  }
}

/* 统计卡片波浪动画 */
.stat-item {
  position: relative;
  overflow: hidden;
}

.stat-item::after {
  content: '';
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: linear-gradient(
    45deg,
    transparent 30%,
    rgba(0, 240, 255, 0.1) 50%,
    transparent 70%
  );
  transform: rotate(45deg);
  animation: waveMove 3s linear infinite;
}

@keyframes waveMove {
  0% {
    transform: translateX(-100%) translateY(-100%) rotate(45deg);
  }
  100% {
    transform: translateX(100%) translateY(100%) rotate(45deg);
  }
}

/* 图片容器发光效果 */
.journey-image {
  position: relative;
}

.journey-image::before {
  content: '';
  position: absolute;
  top: -5px;
  left: -5px;
  right: -5px;
  bottom: -5px;
  background: linear-gradient(45deg, var(--primary-color), var(--secondary-color), var(--primary-color));
  border-radius: 15px;
  z-index: -1;
  opacity: 0;
  transition: opacity 0.3s ease;
  animation: borderRotate 3s linear infinite;
}

.journey-item:hover .journey-image::before {
  opacity: 1;
}

@keyframes borderRotate {
  0% {
    filter: hue-rotate(0deg);
  }
  100% {
    filter: hue-rotate(360deg);
  }
}

/* 内容卡片闪光效果 */
.journey-content {
  position: relative;
  overflow: hidden;
}

.journey-content::after {
  content: '';
  position: absolute;
  top: -50%;
  left: -50%;
  width: 200%;
  height: 200%;
  background: linear-gradient(
    to right,
    transparent 0%,
    rgba(255, 255, 255, 0.1) 50%,
    transparent 100%
  );
  transform: rotate(30deg);
  transition: all 0.6s;
  opacity: 0;
}

.journey-content:hover::after {
  animation: shimmer 1.5s ease-in-out;
}

@keyframes shimmer {
  0% {
    left: -50%;
    opacity: 0;
  }
  50% {
    opacity: 1;
  }
  100% {
    left: 150%;
    opacity: 0;
  }
}

/* 标题淡入动画 */
.animate-fade-in {
  opacity: 0;
  transform: translateY(-30px);
  transition: opacity 1s ease, transform 1s ease;
}

.animate-fade-in.is-visible {
  opacity: 1;
  transform: translateY(0);
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

/* 滚动触发动画 */
.animate-on-scroll {
  opacity: 0;
  transform: translateY(40px);
  transition: opacity 0.6s ease, transform 0.6s ease;
}

.animate-on-scroll.is-visible {
  opacity: 1;
  transform: translateY(0);
}

/* 时间线圆点脉冲动画 */
.journey-item::before {
  content: '';
  position: absolute;
  left: -8px;
  top: 20px;
  width: 16px;
  height: 16px;
  background: linear-gradient(135deg, var(--primary-color), var(--secondary-color));
  border-radius: 50%;
  box-shadow: 0 0 15px rgba(0, 240, 255, 0.6);
  border: 3px solid var(--bg-darker);
  z-index: 1;
  animation: pulse 2s ease-in-out infinite;
}

@keyframes pulse {
  0%, 100% {
    box-shadow: 0 0 15px rgba(0, 240, 255, 0.6);
    transform: scale(1);
  }
  50% {
    box-shadow: 0 0 25px rgba(0, 240, 255, 0.9);
    transform: scale(1.1);
  }
}

/* 时间线渐入动画 */
.journey-timeline::before {
  content: '';
  position: absolute;
  left: 50px;
  top: 0;
  bottom: 0;
  width: 3px;
  background: linear-gradient(180deg, var(--primary-color), var(--secondary-color));
  box-shadow: 0 0 15px rgba(0, 240, 255, 0.5);
  animation: glowLine 3s ease-in-out infinite alternate;
}

@keyframes glowLine {
  0% {
    box-shadow: 0 0 15px rgba(0, 240, 255, 0.5);
  }
  100% {
    box-shadow: 0 0 25px rgba(0, 240, 255, 0.8), 0 0 35px rgba(0, 240, 255, 0.4);
  }
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

.animate-fade-in.is-visible + .section-subtitle,
.animate-fade-in.is-visible.section-title::after {
  width: 100px;
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

.journey-intro {
  max-width: 900px;
  margin: 0 auto 4rem;
  padding: 2.5rem;
  background: linear-gradient(135deg, var(--bg-card) 0%, rgba(18, 24, 41, 0.6) 100%);
  border-radius: 16px;
  border: 1px solid rgba(0, 240, 255, 0.2);
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

.intro-text:nth-child(1) {
  animation-delay: 0.2s;
}

.intro-text:nth-child(2) {
  animation-delay: 0.4s;
}

@keyframes fadeSlideIn {
  from {
    opacity: 0;
    transform: translateX(-20px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

.intro-text:last-child {
  margin-bottom: 0;
}

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
  box-shadow: 0 0 15px rgba(0, 240, 255, 0.5);
}

.journey-item {
  display: flex;
  gap: 2rem;
  margin-bottom: 3rem;
  position: relative;
  padding-left: 30px;
}

.journey-item:nth-child(even) {
  flex-direction: row-reverse;
}

.journey-item:nth-child(even)::before {
  left: auto;
  right: -8px;
}

.journey-image {
  flex: 0 0 400px;
}

.journey-image img {
  width: 100%;
  height: auto;
  border-radius: 12px;
  border: 2px solid rgba(0, 240, 255, 0.3);
  box-shadow: 0 0 20px rgba(0, 240, 255, 0.3);
  transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  opacity: 0.9;
}

.journey-image img:hover {
  transform: scale(1.05) rotate(1deg);
  box-shadow: 0 0 40px rgba(0, 240, 255, 0.7);
  opacity: 1;
}

.journey-content {
  flex: 1;
  background: linear-gradient(135deg, var(--bg-card) 0%, rgba(18, 24, 41, 0.6) 100%);
  border-radius: 12px;
  padding: 1.5rem;
  border: 1px solid rgba(0, 240, 255, 0.1);
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
  background: linear-gradient(90deg, transparent, var(--primary-color), transparent);
  transform: translateX(-100%);
  transition: transform 0.6s ease;
}

.journey-content:hover::before {
  transform: translateX(0);
}

.journey-content:hover {
  border-color: rgba(0, 240, 255, 0.4);
  box-shadow: var(--shadow-lg), 0 0 30px rgba(0, 240, 255, 0.2);
  transform: translateX(5px);
}

.journey-item:nth-child(even) .journey-content:hover {
  transform: translateX(-5px);
}

.journey-title {
  font-size: 1.4rem;
  font-weight: 700;
  color: var(--primary-color);
  margin-bottom: 1rem;
  text-shadow: var(--glow-text);
  position: relative;
  display: inline-block;
}

.journey-title::after {
  content: '';
  position: absolute;
  bottom: -2px;
  left: 0;
  width: 0;
  height: 2px;
  background: linear-gradient(90deg, var(--primary-color), var(--secondary-color));
  transition: width 0.4s ease;
}

.journey-content:hover .journey-title::after {
  width: 100%;
}

.journey-text {
  color: var(--text-light);
  line-height: 1.9;
  font-size: 1rem;
}

.journey-stats {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 2rem;
  max-width: 800px;
  margin: 0 auto;
}

.stat-item {
  text-align: center;
  padding: 2rem 1rem;
  background: linear-gradient(135deg, var(--bg-card) 0%, rgba(18, 24, 41, 0.6) 100%);
  border-radius: 16px;
  border: 1px solid rgba(0, 240, 255, 0.1);
  transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  position: relative;
  overflow: hidden;
}

.stat-item::before {
  content: '';
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(90deg, transparent, rgba(0, 240, 255, 0.1), transparent);
  transition: left 0.6s ease;
}

.stat-item:hover::before {
  left: 100%;
}

.stat-item:hover {
  transform: translateY(-12px) scale(1.02);
  box-shadow: var(--shadow-lg), 0 0 30px rgba(0, 240, 255, 0.3);
  border-color: rgba(0, 240, 255, 0.4);
}

.stat-number {
  font-size: 2.5rem;
  font-weight: 700;
  color: var(--primary-color);
  text-shadow: var(--glow-text);
  margin-bottom: 0.5rem;
  transition: all 0.3s ease;
}

.stat-item:hover .stat-number {
  transform: scale(1.1);
  text-shadow: 0 0 20px rgba(0, 240, 255, 0.8), 0 0 40px rgba(0, 240, 255, 0.4);
}

.stat-label {
  color: var(--text-light);
  font-size: 0.95rem;
}

@media (max-width: 900px) {
  .journey-timeline::before {
    left: 20px;
  }

  .journey-item {
    flex-direction: column !important;
    padding-left: 50px;
  }

  .journey-item::before {
    left: 12px !important;
    right: auto !important;
  }

  .journey-image {
    flex: none;
    width: 100%;
  }

  .journey-title {
    font-size: 1.2rem;
  }

  .journey-stats {
    grid-template-columns: repeat(2, 1fr);
    gap: 1rem;
  }

  .stat-number {
    font-size: 2rem;
  }
}

/* C++特殊特效 */
.cpp-special .journey-image {
  position: relative;
  overflow: visible;
}

.cpp-image-wrapper {
  position: relative;
}

.cpp-glow {
  position: relative;
  z-index: 2;
  animation: cppFloat 3s ease-in-out infinite;
  filter: drop-shadow(0 0 10px rgba(0, 255, 136, 0.5));
}

@keyframes cppFloat {
  0%, 100% {
    transform: translateY(0) scale(1);
  }
  50% {
    transform: translateY(-10px) scale(1.02);
  }
}

.cpp-image-wrapper:hover .cpp-glow {
  animation: cppSpin 0.6s ease-in-out;
  filter: drop-shadow(0 0 20px rgba(0, 255, 136, 0.8)) drop-shadow(0 0 40px rgba(0, 255, 136, 0.4));
}

@keyframes cppSpin {
  0% {
    transform: rotate(0deg) scale(1);
  }
  50% {
    transform: rotate(5deg) scale(1.05);
  }
  100% {
    transform: rotate(0deg) scale(1);
  }
}

/* 代码雨效果 */
.code-rain {
  position: absolute;
  width: 2px;
  height: 20px;
  background: linear-gradient(180deg, transparent, #00ff88, transparent);
  opacity: 0;
  z-index: 1;
}

.code-rain:nth-child(1) {
  left: 10%;
  animation: rainFall 2s linear infinite;
  animation-delay: 0s;
}

.code-rain:nth-child(2) {
  left: 50%;
  animation: rainFall 2s linear infinite;
  animation-delay: 0.5s;
}

.code-rain:nth-child(3) {
  left: 80%;
  animation: rainFall 2s linear infinite;
  animation-delay: 1s;
}

@keyframes rainFall {
  0% {
    top: -20px;
    opacity: 0;
  }
  10% {
    opacity: 1;
  }
  90% {
    opacity: 1;
  }
  100% {
    top: 100%;
    opacity: 0;
  }
}

.cpp-image-wrapper:hover .code-rain {
  animation-duration: 1s;
}

/* 打字机效果 */
.typing-effect {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  font-family: 'Courier New', monospace;
  font-size: 1.2rem;
  font-weight: bold;
  color: #00ff88;
  text-shadow: 0 0 10px rgba(0, 255, 136, 0.8);
  opacity: 0;
  z-index: 3;
  pointer-events: none;
  white-space: nowrap;
}

.cpp-image-wrapper:hover .typing-effect {
  animation: typingReveal 0.5s ease forwards;
}

@keyframes typingReveal {
  0% {
    opacity: 0;
    transform: translate(-50%, -50%) scale(0.5);
  }
  50% {
    opacity: 1;
    transform: translate(-50%, -50%) scale(1.1);
  }
  100% {
    opacity: 1;
    transform: translate(-50%, -50%) scale(1);
  }
}

/* C++标题特殊样式 */
.cpp-special .journey-title {
  background: linear-gradient(90deg, #00ff88, #00d4ff);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  background-clip: text;
  animation: titleGlow 2s ease-in-out infinite alternate;
}

@keyframes titleGlow {
  0% {
    text-shadow: 0 0 10px rgba(0, 255, 136, 0.5);
  }
  100% {
    text-shadow: 0 0 20px rgba(0, 255, 136, 0.8), 0 0 30px rgba(0, 212, 255, 0.6);
  }
}

/* 脉冲边框 */
.cpp-special .journey-content {
  border: 1px solid rgba(0, 255, 136, 0.2);
}

.cpp-special:hover .journey-content {
  border-color: rgba(0, 255, 136, 0.5);
  animation: borderPulse 1s ease-in-out;
}

@keyframes borderPulse {
  0%, 100% {
    box-shadow: var(--shadow-lg), 0 0 0 0 rgba(0, 255, 136, 0.4);
  }
  50% {
    box-shadow: var(--shadow-lg), 0 0 0 10px rgba(0, 255, 136, 0);
  }
}
</style>
