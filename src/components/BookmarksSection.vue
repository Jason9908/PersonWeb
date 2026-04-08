<template>
  <section id="bookmarks" class="bookmarks">
    <h2 class="section-title">我的收藏</h2>
    <p class="section-subtitle">
      常用学习资源、开发工具和技术社区 - 导入自浏览器收藏夹
    </p>

    <div class="bookmarks-layout">
      <!-- 左侧分类列表 -->
      <div class="category-sidebar">
        <div
          :class="['category-item', { active: activeCategory === 'all' }]"
          @click="activeCategory = 'all'"
        >
          <span class="cat-icon">📚</span>
          <span class="cat-name">全部</span>
          <span class="cat-count">{{ totalCount }}</span>
        </div>
        <div
          v-for="cat in categories"
          :key="cat.id"
          :class="['category-item', { active: activeCategory === cat.id }]"
          @click="activeCategory = cat.id"
        >
          <span class="cat-icon">{{ cat.icon }}</span>
          <span class="cat-name">{{ cat.name }}</span>
          <span class="cat-count">{{ cat.links.length }}</span>
        </div>
      </div>

      <!-- 右侧内容区 -->
      <div class="content-area">
        <div v-if="activeCategory === 'all'" class="all-categories">
          <div
            v-for="category in categories"
            :key="category.id"
            class="bookmark-category"
          >
            <div class="category-header">
              <span class="category-icon">{{ category.icon }}</span>
              <h3 class="category-name">{{ category.name }}</h3>
              <span class="category-count">{{ category.links.length }} 个</span>
            </div>
            <ul class="bookmark-list">
              <li v-for="(link, index) in category.links" :key="index" class="bookmark-item">
                <a
                  :href="link.url"
                  target="_blank"
                  rel="noopener noreferrer"
                  class="bookmark-link"
                >
                  <div class="bookmark-info">
                    <h4 class="bookmark-name">{{ link.name }}</h4>
                    <p class="bookmark-description">{{ link.description }}</p>
                  </div>
                  <span class="bookmark-arrow">→</span>
                </a>
              </li>
            </ul>
          </div>
        </div>

        <div v-else class="category-detail">
          <div class="detail-header">
            <span class="detail-icon">{{ currentCategory.icon }}</span>
            <h2 class="detail-title">{{ currentCategory.name }}</h2>
            <span class="category-count">{{ currentCategory.links.length }} 个</span>
          </div>

          <ul class="bookmark-list">
            <li v-for="(link, index) in currentCategory.links" :key="index" class="bookmark-item">
              <a
                :href="link.url"
                target="_blank"
                rel="noopener noreferrer"
                class="bookmark-link"
              >
                <div class="bookmark-info">
                  <h4 class="bookmark-name">{{ link.name }}</h4>
                  <p class="bookmark-description">{{ link.description }}</p>
                </div>
                <span class="bookmark-arrow">→</span>
              </a>
            </li>
          </ul>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, computed } from 'vue'

const activeCategory = ref('learning')

const categories = [
  {
    id: 'learning',
    name: '编程学习',
    icon: '📚',
    fullDescription: '精选编程学习资源，包括CSDN、博客园、廖雪峰等知名技术博客和教程网站，涵盖Python、Java、C语言等多门编程语言。',
    links: [
      { name: 'CSDN', url: 'https://Jasonakeke.blog.csdn.net', description: '我的技术主场 | 全栈与IoT硬核干货' },
      { name: '博客园', url: 'https://www.cnblogs.com', description: '老牌技术社区 | 开发者精神家园' },
      { name: '廖雪峰', url: 'https://www.liaoxuefeng.com', description: '编程圣经 | Python/Java/Git终极教程' },
      { name: 'C语言中文网', url: 'http://c.biancheng.net', description: 'C/C++修炼手册 | 从入门到精通' },
      { name: 'Linux命令', url: 'https://www.linuxcool.com', description: '终端神器 | 命令速查宝典' },
      { name: 'JavaGuide', url: 'https://snailclimb.top/JavaGuide', description: 'Java通关秘籍 | 面试收割机' }
    ]
  },
  {
    id: 'tools',
    name: '开发工具',
    icon: '🛠️',
    fullDescription: '必备开发工具集合，包括GitHub、Gitee等代码托管平台，JetBrains IDE，Stack Overflow问答社区，以及MDN等权威开发文档。',
    links: [
      { name: 'GitHub', url: 'https://github.com', description: '全球代码宇宙 | 开源圣地' },
      { name: 'Gitee', url: 'https://gitee.com', description: '国产代码托管 | 极速访问' },
      { name: 'JetBrains', url: 'https://www.jetbrains.com', description: 'IDE之王 | 开发装备库' },
      { name: 'Stack Overflow', url: 'https://stackoverflow.com', description: '程序员终极问答 | Bug终结者' },
      { name: 'MDN Web文档', url: 'https://developer.mozilla.org', description: 'Web开发圣经 | 前端权威指南' },
      { name: 'SegmentFault', url: 'https://segmentfault.com', description: '中文技术社区 | 思维碰撞地' }
    ]
  },
  {
    id: 'online-tools',
    name: '在线工具',
    icon: '⚡',
    fullDescription: '便捷的在线开发工具，包括ProcessOn流程图、Excalidraw白板、在线JSON格式化、Carbon代码美图等实用工具，提高开发效率。',
    links: [
      { name: 'ProcessOn', url: 'https://www.processon.com', description: '思维可视化 | 创意落地神器' },
      { name: 'Excalidraw', url: 'https://excalidraw.com', description: '手绘风白板 | 协作黑科技' },
      { name: '在线工具', url: 'https://tool.lu', description: '极客工具箱 | 开发者外挂' },
      { name: 'JSON在线', url: 'https://www.sojson.com', description: '数据调教师 | 格式化利器' },
      { name: 'Carbon', url: 'https://carbon.now.sh', description: '代码美学大师 | 极客装逼神器' },
      { name: 'ColorHunt', url: 'https://colorhunt.co', description: '配色灵感库 | 视觉美学加油站' }
    ]
  },
  {
    id: 'platforms',
    name: '学习平台',
    icon: '🎓',
    fullDescription: '优质IT学习平台，包括慕课网、网易云课堂、中国大学MOOC等，提供系统的编程课程和视频教程，适合不同阶段的学习者。',
    links: [
      { name: '慕课网', url: 'https://www.imooc.com', description: 'IT技能修炼场 | 实战派训练营' },
      { name: '网易云课堂', url: 'https://study.163.com', description: '知识宝库 | 终身学习充电站' },
      { name: '学堂在线', url: 'https://next.xuetangx.com', description: '清华血统 | 顶级学府课程' },
      { name: 'MOOC', url: 'https://www.icourse163.org', description: '中国大学MOOC | 高材生之路' },
      { name: 'B站', url: 'https://www.bilibili.com', description: '学习网站 | 程序员快乐源泉' },
      { name: '牛客网', url: 'https://www.nowcoder.com', description: '求职神器 | 大厂收割机' }
    ]
  },
  {
    id: 'resources',
    name: '技术资源',
    icon: '📖',
    fullDescription: '常用技术文档和资源库，包括ECharts数据可视化、Vue.js框架、jQuery库等技术文档，以及力扣等算法学习平台。',
    links: [
      { name: 'Apache ECharts', url: 'https://www.echartsjs.com', description: '数据可视化神器 | 百度开源力作' },
      { name: 'Vue.js', url: 'https://cn.vuejs.org', description: '渐进式框架 | 前端魔法棒' },
      { name: 'jQuery', url: 'https://jquery.com', description: 'JS经典库 | 永恒传奇' },
      { name: 'EasyX文档', url: 'https://docs.easyx.cn', description: 'C语言图形库 | 游戏启蒙导师' },
      { name: 'Qt', url: 'https://blog.csdn.net/lg930320', description: '跨平台王者 | 桌面开发神器' },
      { name: '力扣', url: 'https://leetcode-cn.com', description: '算法竞技场 | 编程思维健身房' }
    ]
  },
  {
    id: 'community',
    name: '技术社区',
    icon: '👥',
    fullDescription: '活跃的技术开发者社区，包括OSCHINA开源社区、InfoQ技术前沿、51CTO技术分享等，获取最新技术资讯和经验交流。',
    links: [
      { name: 'OSCHINA', url: 'https://www.oschina.net', description: '开源中国 | 技术风向标' },
      { name: 'InfoQ', url: 'https://www.infoq.com', description: '技术趋势洞察 | 前沿瞭望塔' },
      { name: '51CTO', url: 'https://www.51cto.com', description: '技术弹药库 | 硬核内容集合地' },
      { name: '脚本之家', url: 'https://www.jb51.net', description: '代码军火库 | 脚本资源大本营' },
      { name: '图灵社区', url: 'https://www.ituring.com.cn', description: '图书殿堂 | 技术思想高地' },
      { name: '云栖社区', url: 'https://yq.aliyun.com', description: '阿里云技术社区 | 云计算领航者' }
    ]
  },
  {
    id: 'career',
    name: '求职考试',
    icon: '💼',
    fullDescription: '程序员求职和考试相关资源，包括学信网学历查询、考研帮、软考考试、程序员客栈等，助力职业发展。',
    links: [
      { name: '学信网', url: 'https://www.chsi.com.cn', description: '学历权威认证 | 学籍身份验证' },
      { name: '考研帮', url: 'http://www.kaoyan.com', description: '考研集结地 | 学历进阶之路' },
      { name: '软考', url: 'http://www.ruankao.org.cn', description: '国家级IT认证 | 职称晋升通道' },
      { name: '程序员客栈', url: 'https://www.proginn.com', description: '自由职业天堂 | 远程工作营地' },
      { name: '牛耳', url: 'http://www.newer2001.com', description: 'IT职业教育 | 实战技能加速器' },
      { name: '大鹏教育', url: 'https://www.dapengjiaoyu.cn', description: '在线IT培训 | 职业起飞跑道' }
    ]
  },
  {
    id: 'other',
    name: '其他收藏',
    icon: '🔖',
    fullDescription: '其他实用网站收藏，包括破局行动个人成长社区、小鹅通知识付费工具、百度脑图在线思维导图等实用工具。',
    links: [
      { name: '破局行动', url: 'https://aipoju.com/action', description: '个人成长社区 | 自律进化基地' },
      { name: '小鹅通', url: 'https://study.xiaoe-tech.com', description: '知识变现引擎 | 课程店铺搭建神器' },
      { name: '百度脑图', url: 'https://naotu.baidu.com', description: '思维导图利器 | 创意可视化' },
      { name: '去背景', url: 'https://www.remove.bg', description: 'AI黑科技 | 一键抠图魔法' },
      { name: 'icon', url: 'http://www.easyicon.net', description: '图标弹药库 | 视觉设计素材库' },
      { name: 'Google', url: 'https://www.google.hk', description: '终极搜索引擎 | 技术问题解答器' }
    ]
  }
]

const currentCategory = computed(() => {
  if (activeCategory.value === 'all') {
    return { links: [], fullDescription: '' }
  }
  return categories.find(c => c.id === activeCategory.value) || categories[0]
})

const totalCount = computed(() => {
  return categories.reduce((sum, cat) => sum + cat.links.length, 0)
})
</script>

<style scoped>
.bookmarks {
  background-color: var(--bg-dark);
  padding: 80px 0;
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

.bookmarks-layout {
  max-width: 1200px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 280px 1fr;
  gap: 2rem;
  align-items: start;
}

/* 左侧分类列表 */
.category-sidebar {
  background: rgba(18, 24, 41, 0.6);
  border-radius: 16px;
  padding: 1rem;
  border: 1px solid rgba(0, 240, 255, 0.1);
  position: sticky;
  top: 100px;
}

.category-item {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  padding: 0.875rem 1rem;
  border-radius: 12px;
  cursor: pointer;
  transition: all 0.3s ease;
  margin-bottom: 0.5rem;
  border: 1px solid transparent;
}

.category-item:hover {
  background: rgba(0, 240, 255, 0.1);
  border-color: rgba(0, 240, 255, 0.2);
}

.category-item.active {
  background: linear-gradient(135deg, rgba(0, 240, 255, 0.2), rgba(123, 44, 191, 0.2));
  border-color: var(--primary-color);
  box-shadow: 0 0 20px rgba(0, 240, 255, 0.3);
}

.cat-icon {
  font-size: 1.5rem;
  flex-shrink: 0;
}

.cat-name {
  flex: 1;
  font-size: 0.95rem;
  font-weight: 500;
  color: var(--text-dark);
}

.cat-count {
  font-size: 0.75rem;
  color: var(--text-light);
  background: rgba(0, 240, 255, 0.1);
  padding: 0.2rem 0.5rem;
  border-radius: 10px;
}

/* 右侧内容区 */
.content-area {
  min-height: 600px;
}

.all-categories {
  display: grid;
  grid-template-columns: repeat(auto-fill, minmax(320px, 1fr));
  gap: 2rem;
}

.category-detail {
  background: rgba(18, 24, 41, 0.6);
  border-radius: 16px;
  padding: 1.5rem;
  border: 1px solid rgba(0, 240, 255, 0.1);
}

.detail-header {
  display: flex;
  align-items: center;
  gap: 1rem;
  margin-bottom: 1.5rem;
  padding-bottom: 1rem;
  border-bottom: 2px solid rgba(0, 240, 255, 0.1);
}

.detail-icon {
  font-size: 2rem;
  filter: drop-shadow(0 0 5px var(--primary-color));
}

.detail-title {
  font-size: 1.5rem;
  font-weight: 700;
  color: var(--text-dark);
  margin: 0;
  flex: 1;
}

/* 书签卡片样式 */
.bookmark-category {
  background: linear-gradient(135deg, var(--bg-card) 0%, rgba(18, 24, 41, 0.6) 100%);
  border-radius: 16px;
  padding: 1.5rem;
  border: 1px solid rgba(0, 240, 255, 0.1);
  transition: transform 0.3s ease, box-shadow 0.3s ease;
  animation: fadeIn 0.3s ease;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.bookmark-category:hover {
  transform: translateY(-4px);
  box-shadow: var(--shadow-lg);
  border-color: rgba(0, 240, 255, 0.2);
}

.category-header {
  display: flex;
  align-items: center;
  gap: 0.75rem;
  margin-bottom: 1.5rem;
  padding-bottom: 1rem;
  border-bottom: 2px solid rgba(0, 240, 255, 0.1);
}

.category-icon {
  font-size: 1.8rem;
  filter: drop-shadow(0 0 5px var(--primary-color));
}

.category-name {
  font-size: 1.25rem;
  font-weight: 700;
  color: var(--text-dark);
  flex: 1;
}

.category-count {
  font-size: 0.8rem;
  color: var(--text-light);
  background: rgba(0, 240, 255, 0.1);
  padding: 0.25rem 0.75rem;
  border-radius: 12px;
  font-weight: 500;
  border: 1px solid rgba(0, 240, 255, 0.2);
}

.bookmark-list {
  list-style: none;
  padding: 0;
  margin: 0;
}

.bookmark-item {
  margin-bottom: 0.75rem;
}

.bookmark-item:last-child {
  margin-bottom: 0;
}

.bookmark-link {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0.75rem;
  background: rgba(10, 14, 39, 0.6);
  border-radius: 10px;
  border: 1px solid rgba(0, 240, 255, 0.1);
  transition: all 0.3s ease;
  text-decoration: none;
}

.bookmark-link:hover {
  background: linear-gradient(135deg, rgba(0, 240, 255, 0.2), rgba(123, 44, 191, 0.2));
  border-color: var(--primary-color);
  transform: translateX(4px);
  box-shadow: 0 0 15px rgba(0, 240, 255, 0.2);
}

.bookmark-link:hover .bookmark-description {
  color: rgba(255, 255, 255, 0.85);
}

.bookmark-link:hover .bookmark-arrow {
  transform: translateX(4px);
  text-shadow: var(--glow-text);
}

.bookmark-info {
  flex: 1;
  min-width: 0;
}

.bookmark-name {
  font-size: 1rem;
  font-weight: 600;
  margin: 0 0 0.25rem 0;
  color: var(--text-dark);
  transition: color 0.3s ease;
}

.bookmark-link:hover .bookmark-name {
  color: var(--primary-color);
}

.bookmark-description {
  font-size: 0.8rem;
  color: var(--text-light);
  transition: color 0.3s ease;
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
  margin: 0;
}

.bookmark-arrow {
  font-size: 1.25rem;
  color: var(--primary-color);
  transition: transform 0.3s ease;
  flex-shrink: 0;
  margin-left: 0.5rem;
}

@media (max-width: 968px) {
  .bookmarks-layout {
    grid-template-columns: 1fr;
  }

  .category-sidebar {
    position: static;
  }

  .all-categories {
    grid-template-columns: 1fr;
  }

  .detail-header {
    flex-direction: column;
    text-align: center;
  }

  .detail-icon {
    font-size: 2.5rem;
  }

  .detail-title {
    font-size: 1.5rem;
  }
}
</style>
