<template>
  <section id="bookmarks" class="bookmarks">
    <h2 class="section-title">我的收藏</h2>
    <p class="section-subtitle">
      常用学习资源、开发工具和技术社区 - 导入自浏览器收藏夹
    </p>

    <div class="bookmarks-layout">
      <!-- 左侧分类列表 -->
      <div class="category-sidebar">
        <!-- 场景筛选 -->
        <div class="scene-filters">
          <span class="scene-label">场景筛选</span>
          <div class="scene-tabs">
            <button
              :class="['scene-tab', { active: activeScene === 'all' }]"
              @click="activeScene = 'all'"
            >
              全部推荐
            </button>
            <button
              :class="['scene-tab', { active: activeScene === 'beginner' }]"
              @click="activeScene = 'beginner'"
            >
              新手入门
            </button>
            <button
              :class="['scene-tab', { active: activeScene === 'advanced' }]"
              @click="activeScene = 'advanced'"
            >
              进阶提升
            </button>
            <button
              :class="['scene-tab', { active: activeScene === 'interview' }]"
              @click="activeScene = 'interview'"
            >
              求职面试
            </button>
          </div>
        </div>

        <div class="category-divider"></div>

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
            v-for="category in filteredCategories"
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
                    <div v-if="activeScene === 'all'" class="link-scenes">
                      <span
                        v-for="scene in link.scenes"
                        :key="scene"
                        :class="['scene-tag', scene]"
                      >
                        {{ sceneTags[scene] }}
                      </span>
                    </div>
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
                  <div v-if="activeScene === 'all'" class="link-scenes">
                    <span
                      v-for="scene in link.scenes"
                      :key="scene"
                      :class="['scene-tag', scene]"
                    >
                      {{ sceneTags[scene] }}
                    </span>
                  </div>
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

const activeCategory = ref('all')
const activeScene = ref('all')

// 场景标签定义
const sceneTags = {
  beginner: '新手入门',
  advanced: '进阶提升',
  interview: '求职面试'
}

// 为链接添加场景标签
const taggedCategories = [
  {
    id: 'learning',
    name: '编程学习',
    icon: '📚',
    fullDescription: '精选编程学习资源，包括CSDN、博客园、廖雪峰等知名技术博客和教程网站，涵盖Python、Java、C语言等多门编程语言。',
    links: [
      { name: 'CSDN', url: 'https://Jasonakeke.blog.csdn.net', description: '我的技术主场 | 全栈与IoT硬核干货', scenes: ['beginner', 'advanced', 'interview'] },
      { name: '博客园', url: 'https://www.cnblogs.com', description: '老牌技术社区 | 开发者精神家园', scenes: ['beginner', 'advanced'] },
      { name: '廖雪峰', url: 'https://www.liaoxuefeng.com', description: '编程圣经 | Python/Java/Git终极教程', scenes: ['beginner', 'advanced'] },
      { name: 'C语言中文网', url: 'http://c.biancheng.net', description: 'C/C++修炼手册 | 从入门到精通', scenes: ['beginner'] },
      { name: 'Linux命令', url: 'https://www.linuxcool.com', description: '终端神器 | 命令速查宝典', scenes: ['advanced'] },
      { name: 'JavaGuide', url: 'https://snailclimb.top/JavaGuide', description: 'Java通关秘籍 | 面试收割机', scenes: ['interview'] }
    ]
  },
  {
    id: 'tools',
    name: '开发工具',
    icon: '🛠️',
    fullDescription: '必备开发工具集合，包括GitHub、Gitee等代码托管平台，JetBrains IDE，Stack Overflow问答社区，以及MDN等权威开发文档。',
    links: [
      { name: 'GitHub', url: 'https://github.com', description: '全球代码宇宙 | 开源圣地', scenes: ['beginner', 'advanced', 'interview'] },
      { name: 'Gitee', url: 'https://gitee.com', description: '国产代码托管 | 极速访问', scenes: ['beginner'] },
      { name: 'JetBrains', url: 'https://www.jetbrains.com', description: 'IDE之王 | 开发装备库', scenes: ['beginner', 'advanced'] },
      { name: 'Stack Overflow', url: 'https://stackoverflow.com', description: '程序员终极问答 | Bug终结者', scenes: ['advanced', 'interview'] },
      { name: 'MDN Web文档', url: 'https://developer.mozilla.org', description: 'Web开发圣经 | 前端权威指南', scenes: ['beginner', 'advanced'] },
      { name: 'SegmentFault', url: 'https://segmentfault.com', description: '中文技术社区 | 思维碰撞地', scenes: ['beginner', 'advanced'] }
    ]
  },
  {
    id: 'online-tools',
    name: '在线工具',
    icon: '⚡',
    fullDescription: '便捷的在线开发工具，包括ProcessOn流程图、Excalidraw白板、在线JSON格式化、Carbon代码美图等实用工具，提高开发效率。',
    links: [
      { name: 'ProcessOn', url: 'https://www.processon.com', description: '思维可视化 | 创意落地神器', scenes: ['beginner', 'advanced'] },
      { name: 'Excalidraw', url: 'https://excalidraw.com', description: '手绘风白板 | 协作黑科技', scenes: ['beginner', 'advanced'] },
      { name: '在线工具', url: 'https://tool.lu', description: '极客工具箱 | 开发者外挂', scenes: ['advanced'] },
      { name: 'JSON在线', url: 'https://www.sojson.com', description: '数据调教师 | 格式化利器', scenes: ['beginner', 'advanced'] },
      { name: 'Carbon', url: 'https://carbon.now.sh', description: '代码美学大师 | 极客装逼神器', scenes: ['advanced'] },
      { name: 'ColorHunt', url: 'https://colorhunt.co', description: '配色灵感库 | 视觉美学加油站', scenes: ['beginner'] }
    ]
  },
  {
    id: 'platforms',
    name: '学习平台',
    icon: '🎓',
    fullDescription: '优质IT学习平台，包括慕课网、网易云课堂、中国大学MOOC等，提供系统的编程课程和视频教程，适合不同阶段的学习者。',
    links: [
      { name: '慕课网', url: 'https://www.imooc.com', description: 'IT技能修炼场 | 实战派训练营', scenes: ['beginner', 'advanced'] },
      { name: '网易云课堂', url: 'https://study.163.com', description: '知识宝库 | 终身学习充电站', scenes: ['beginner', 'advanced'] },
      { name: '学堂在线', url: 'https://next.xuetangx.com', description: '清华血统 | 顶级学府课程', scenes: ['advanced'] },
      { name: 'MOOC', url: 'https://www.icourse163.org', description: '中国大学MOOC | 高材生之路', scenes: ['beginner', 'advanced'] },
      { name: 'B站', url: 'https://www.bilibili.com', description: '学习网站 | 程序员快乐源泉', scenes: ['beginner', 'advanced'] },
      { name: '牛客网', url: 'https://www.nowcoder.com', description: '求职神器 | 大厂收割机', scenes: ['interview'] }
    ]
  },
  {
    id: 'resources',
    name: '技术资源',
    icon: '📖',
    fullDescription: '常用技术文档和资源库，包括ECharts数据可视化、Vue.js框架、jQuery库等技术文档，以及力扣等算法学习平台。',
    links: [
      { name: 'Apache ECharts', url: 'https://www.echartsjs.com', description: '数据可视化神器 | 百度开源力作', scenes: ['advanced'] },
      { name: 'Vue.js', url: 'https://cn.vuejs.org', description: '渐进式框架 | 前端魔法棒', scenes: ['beginner', 'advanced'] },
      { name: 'jQuery', url: 'https://jquery.com', description: 'JS经典库 | 永恒传奇', scenes: ['beginner'] },
      { name: 'EasyX文档', url: 'https://docs.easyx.cn', description: 'C语言图形库 | 游戏启蒙导师', scenes: ['beginner'] },
      { name: 'Qt', url: 'https://blog.csdn.net/lg930320', description: '跨平台王者 | 桌面开发神器', scenes: ['advanced'] },
      { name: '力扣', url: 'https://leetcode-cn.com', description: '算法竞技场 | 编程思维健身房', scenes: ['interview'] }
    ]
  },
  {
    id: 'community',
    name: '技术社区',
    icon: '👥',
    fullDescription: '活跃的技术开发者社区，包括OSCHINA开源社区、InfoQ技术前沿、51CTO技术分享等，获取最新技术资讯和经验交流。',
    links: [
      { name: 'OSCHINA', url: 'https://www.oschina.net', description: '开源中国 | 技术风向标', scenes: ['advanced'] },
      { name: 'InfoQ', url: 'https://www.infoq.com', description: '技术趋势洞察 | 前沿瞭望塔', scenes: ['advanced'] },
      { name: '51CTO', url: 'https://www.51cto.com', description: '技术弹药库 | 硬核内容集合地', scenes: ['beginner', 'advanced'] },
      { name: '脚本之家', url: 'https://www.jb51.net', description: '代码军火库 | 脚本资源大本营', scenes: ['beginner', 'advanced'] },
      { name: '图灵社区', url: 'https://www.ituring.com.cn', description: '图书殿堂 | 技术思想高地', scenes: ['advanced'] },
      { name: '云栖社区', url: 'https://yq.aliyun.com', description: '阿里云技术社区 | 云计算领航者', scenes: ['advanced'] }
    ]
  },
  {
    id: 'career',
    name: '求职考试',
    icon: '💼',
    fullDescription: '程序员求职和考试相关资源，包括学信网学历查询、考研帮、软考考试、程序员客栈等，助力职业发展。',
    links: [
      { name: '学信网', url: 'https://www.chsi.com.cn', description: '学历权威认证 | 学籍身份验证', scenes: ['interview'] },
      { name: '考研帮', url: 'http://www.kaoyan.com', description: '考研集结地 | 学历进阶之路', scenes: ['interview'] },
      { name: '软考', url: 'http://www.ruankao.org.cn', description: '国家级IT认证 | 职称晋升通道', scenes: ['interview'] },
      { name: '程序员客栈', url: 'https://www.proginn.com', description: '自由职业天堂 | 远程工作营地', scenes: ['interview'] },
      { name: '牛耳', url: 'http://www.newer2001.com', description: 'IT职业教育 | 实战技能加速器', scenes: ['beginner'] },
      { name: '大鹏教育', url: 'https://www.dapengjiaoyu.cn', description: '在线IT培训 | 职业起飞跑道', scenes: ['beginner'] }
    ]
  },
  {
    id: 'other',
    name: '其他收藏',
    icon: '🔖',
    fullDescription: '其他实用网站收藏，包括破局行动个人成长社区、小鹅通知识付费工具、百度脑图在线思维导图等实用工具。',
    links: [
      { name: '破局行动', url: 'https://aipoju.com/action', description: '个人成长社区 | 自律进化基地', scenes: ['beginner', 'advanced'] },
      { name: '小鹅通', url: 'https://study.xiaoe-tech.com', description: '知识变现引擎 | 课程店铺搭建神器', scenes: ['advanced'] },
      { name: '百度脑图', url: 'https://naotu.baidu.com', description: '思维导图利器 | 创意可视化', scenes: ['beginner', 'advanced'] },
      { name: '去背景', url: 'https://www.remove.bg', description: 'AI黑科技 | 一键抠图魔法', scenes: ['advanced'] },
      { name: 'icon', url: 'http://www.easyicon.net', description: '图标弹药库 | 视觉设计素材库', scenes: ['advanced'] },
      { name: 'Google', url: 'https://www.google.hk', description: '终极搜索引擎 | 技术问题解答器', scenes: ['beginner', 'advanced', 'interview'] }
    ]
  }
]

// 使用taggedCategories替代原来的categories
const categories = taggedCategories

const currentCategory = computed(() => {
  if (activeCategory.value === 'all') {
    return { links: [], fullDescription: '' }
  }
  return categories.find(c => c.id === activeCategory.value) || categories[0]
})

const totalCount = computed(() => {
  return categories.reduce((sum, cat) => sum + cat.links.length, 0)
})

// 根据场景筛选链接
const filteredCategories = computed(() => {
  if (activeScene.value === 'all') {
    return categories
  }
  return categories.map(cat => ({
    ...cat,
    links: cat.links.filter(link => 
      link.scenes && link.scenes.includes(activeScene.value)
    )
  })).filter(cat => cat.links.length > 0)
})

// 场景计数
const sceneCounts = computed(() => {
  const counts = { all: totalCount.value, beginner: 0, advanced: 0, interview: 0 }
  categories.forEach(cat => {
    cat.links.forEach(link => {
      if (link.scenes) {
        link.scenes.forEach(scene => {
          if (counts[scene] !== undefined) {
            counts[scene]++
          }
        })
      }
    })
  })
  return counts
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
  pointer-events: auto;
}

.bookmark-item {
  margin-bottom: 0.75rem;
  pointer-events: auto;
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
  cursor: pointer;
  pointer-events: auto;
  position: relative;
  z-index: 1;
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
  margin: 0;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}

.bookmark-arrow {
  font-size: 1.25rem;
  color: var(--primary-color);
  transition: transform 0.3s ease;
  flex-shrink: 0;
  margin-left: 0.5rem;
}

/* 场景筛选样式 */
.scene-filters {
  margin-bottom: 0.5rem;
}

.scene-label {
  display: block;
  font-size: 0.75rem;
  color: var(--text-light);
  margin-bottom: 0.5rem;
  text-transform: uppercase;
  letter-spacing: 1px;
}

.scene-tabs {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

.scene-tab {
  padding: 0.5rem 0.75rem;
  background: rgba(10, 14, 39, 0.6);
  border: 1px solid rgba(0, 240, 255, 0.1);
  border-radius: 8px;
  color: var(--text-dark);
  font-size: 0.85rem;
  cursor: pointer;
  transition: all 0.3s ease;
  text-align: left;
}

.scene-tab:hover {
  background: rgba(0, 240, 255, 0.1);
  border-color: rgba(0, 240, 255, 0.3);
}

.scene-tab.active {
  background: linear-gradient(135deg, rgba(0, 240, 255, 0.3), rgba(123, 44, 191, 0.3));
  border-color: var(--primary-color);
  color: white;
  font-weight: 600;
}

.category-divider {
  height: 1px;
  background: linear-gradient(90deg, transparent, rgba(0, 240, 255, 0.3), transparent);
  margin: 1rem 0;
}

/* 链接场景标签 */
.link-scenes {
  display: flex;
  flex-wrap: wrap;
  gap: 0.35rem;
  margin-top: 0.5rem;
}

.scene-tag {
  font-size: 0.65rem;
  padding: 0.15rem 0.4rem;
  border-radius: 4px;
  font-weight: 500;
}

.scene-tag.beginner {
  background: rgba(34, 197, 94, 0.2);
  color: #22c55e;
  border: 1px solid rgba(34, 197, 94, 0.3);
}

.scene-tag.advanced {
  background: rgba(59, 130, 246, 0.2);
  color: #3b82f6;
  border: 1px solid rgba(59, 130, 246, 0.3);
}

.scene-tag.interview {
  background: rgba(168, 85, 247, 0.2);
  color: #a855f7;
  border: 1px solid rgba(168, 85, 247, 0.3);
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
