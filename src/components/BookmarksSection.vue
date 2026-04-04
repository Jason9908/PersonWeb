<template>
  <section id="bookmarks" class="bookmarks">
    <h2 class="section-title">收藏网站</h2>
    <p class="section-subtitle">我的常用网站收藏夹</p>

    <div class="bookmarks-wrapper">
      <!-- 左侧树形文件夹 -->
      <div class="bookmarks-tree">
        <div class="tree-content">
          <div class="tree-root">
            <!-- 书签栏 -->
            <div class="tree-item">
              <div
                class="tree-node folder"
                :class="{ expanded: expandedFolders.bookmarksBar, selected: selectedFolder.id === 'bookmarksBar' }"
                @click="toggleFolder('bookmarksBar')"
              >
                <span class="tree-chevron">{{ expandedFolders.bookmarksBar ? '▼' : '▶' }}</span>
                <span class="tree-icon">📁</span>
                <span class="tree-label">书签栏</span>
              </div>
              <div v-if="expandedFolders.bookmarksBar" class="tree-children">
                <!-- 小书签栏 -->
                <div class="tree-item">
                  <div
                    class="tree-node folder"
                    :class="{ expanded: expandedFolders.smallBar, selected: selectedFolder.id === 'smallBar' }"
                    @click="selectFolder('smallBar')"
                  >
                    <span class="tree-chevron">{{ expandedFolders.smallBar ? '▼' : '▶' }}</span>
                    <span class="tree-icon">📁</span>
                    <span class="tree-label">小书签栏</span>
                  </div>
                  <div v-if="expandedFolders.smallBar" class="tree-children">
                    <div class="tree-item">
                      <div
                        class="tree-node folder"
                        :class="{ selected: selectedFolder.id === 'tools' }"
                        @click="selectFolder('tools')"
                      >
                        <span class="tree-icon">📁</span>
                        <span class="tree-label">工具</span>
                      </div>
                    </div>
                    <div class="tree-item">
                      <div
                        class="tree-node folder"
                        :class="{ selected: selectedFolder.id === 'web' }"
                        @click="selectFolder('web')"
                      >
                        <span class="tree-icon">📁</span>
                        <span class="tree-label">网页</span>
                      </div>
                    </div>
                    <div class="tree-item">
                      <div
                        class="tree-node folder"
                        :class="{ selected: selectedFolder.id === 'reading' }"
                        @click="selectFolder('reading')"
                      >
                        <span class="tree-icon">📁</span>
                        <span class="tree-label">阅读</span>
                      </div>
                    </div>
                    <div class="tree-item">
                      <div
                        class="tree-node folder"
                        :class="{ selected: selectedFolder.id === 'text' }"
                        @click="selectFolder('text')"
                      >
                        <span class="tree-icon">📁</span>
                        <span class="tree-label">文字</span>
                      </div>
                    </div>
                    <div class="tree-item">
                      <div
                        class="tree-node folder"
                        :class="{ selected: selectedFolder.id === 'search' }"
                        @click="selectFolder('search')"
                      >
                        <span class="tree-icon">📁</span>
                        <span class="tree-label">搜索</span>
                      </div>
                    </div>
                    <div class="tree-item">
                      <div
                        class="tree-node folder"
                        :class="{ selected: selectedFolder.id === 'searchEngines' }"
                        @click="selectFolder('searchEngines')"
                      >
                        <span class="tree-icon">📁</span>
                        <span class="tree-label">搜索引擎</span>
                      </div>
                    </div>
                    <div class="tree-item">
                      <div
                        class="tree-node folder"
                        :class="{ selected: selectedFolder.id === 'sidebarSearch' }"
                        @click="selectFolder('sidebarSearch')"
                      >
                        <span class="tree-icon">📁</span>
                        <span class="tree-label">边栏搜索</span>
                      </div>
                    </div>
                    <div class="tree-item">
                      <div
                        class="tree-node folder"
                        :class="{ selected: selectedFolder.id === 'links' }"
                        @click="selectFolder('links')"
                      >
                        <span class="tree-icon">📁</span>
                        <span class="tree-label">链接</span>
                      </div>
                    </div>
                    <div class="tree-item">
                      <div
                        class="tree-node folder"
                        :class="{ selected: selectedFolder.id === 'images' }"
                        @click="selectFolder('images')"
                      >
                        <span class="tree-icon">📁</span>
                        <span class="tree-label">图片</span>
                      </div>
                    </div>
                    <div class="tree-item">
                      <div
                        class="tree-node folder"
                        :class="{ selected: selectedFolder.id === 'design' }"
                        @click="selectFolder('design')"
                      >
                        <span class="tree-icon">📁</span>
                        <span class="tree-label">设计</span>
                      </div>
                    </div>
                    <div class="tree-item">
                      <div
                        class="tree-node folder"
                        :class="{ selected: selectedFolder.id === 'development' }"
                        @click="selectFolder('development')"
                      >
                        <span class="tree-icon">📁</span>
                        <span class="tree-label">开发</span>
                      </div>
                    </div>
                  </div>
                </div>
                <!-- 已导入 -->
                <div class="tree-item">
                  <div
                    class="tree-node folder"
                    :class="{ selected: selectedFolder.id === 'imported' }"
                    @click="selectFolder('imported')"
                  >
                    <span class="tree-icon">📁</span>
                    <span class="tree-label">已导入</span>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>

      <!-- 右侧详细内容 -->
      <div class="bookmarks-detail">
        <div class="detail-header">
          <h3 class="detail-title">{{ selectedFolder.name }}</h3>
        </div>
        <div class="detail-content">
          <div
            v-for="bookmark in selectedFolder.items"
            :key="bookmark.url"
            class="detail-item"
          >
            <div class="detail-icon">{{ bookmark.icon }}</div>
            <div class="detail-info">
              <a :href="bookmark.url" target="_blank" class="detail-name">{{ bookmark.name }}</a>
              <span class="detail-url">{{ bookmark.url }}</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref } from 'vue'

const expandedFolders = ref({
  bookmarksBar: true,
  smallBar: true
})

const selectedFolder = ref({
  id: 'smallBar',
  name: '小书签栏',
  items: [
    { name: 'Windows 12 网页版', url: 'http://p.xiaodu0.com/desktop.html', icon: '🖥️' },
    { name: '小鹅通学员版', url: 'https://study.xiaoe-tech.com/t_l/learnIndex?type=wx#/muti_index', icon: '📚' },
    { name: 'RunningCheese使用说明', url: 'https://www.runningcheese.com/bookmarklets', icon: '🧀' },
    { name: '─────────────', url: 'https://separator.mayastudios.com/index.php?t=horz#', icon: '─' },
    { name: '分隔符', url: 'https://separator.mayastudios.com/index.php?t=horz', icon: '➗' },
    { name: '多标签搜索', url: 'https://www.runningcheese.com/multi-search', icon: '🔍' },
    { name: '边栏搜索', url: 'https://www.runningcheese.com/sidebar-search', icon: '🔍' },
    { name: '破局行动', url: 'https://aipoju.com/action', icon: '🎯' },
    { name: '尚硅谷Java', url: 'https://pan.baidu.com/share/init?surl=PhTeMkX5vOg0ZRcw0abjCw&pwd=yyds', icon: '📦' },
    { name: 'Excalidraw', url: 'https://excalidraw.com', icon: '✏️' },
    { name: 'Google', url: 'https://www.google.com.hk/webhp?hl=zh-CN&sourceid=cnhp&gws_rd=ssl', icon: '🔍' },
    { name: 'Adobe', url: 'https://www.adobe.com', icon: '🎨' },
    { name: 'Java快捷键', url: 'https://blog.csdn.net/qq_40272386/article/details/80576813', icon: '⌨️' },
    { name: 'Linux命令', url: 'https://www.linuxcool.com/?from=singlemessage', icon: '🐧' },
    { name: 'C语言中文网', url: 'http://c.biancheng.net', icon: '📖' },
    { name: 'Java视频', url: 'https://study.163.com/course/courseLearn.htm?courseId=343001', icon: '🎬' },
    { name: 'Keil5', url: 'https://blog.csdn.net/cheapter/article/details/80198168', icon: '🔧' },
    { name: 'STM', url: 'https://www.st.com/content/st_com/en.html', icon: '🔧' },
    { name: 'Linux终端', url: 'https://mp.weixin.qq.com/s/yI6rQIVk0Z4zIXrQAiqnmQ', icon: '💻' },
    { name: '搜狐视频', url: 'https://tv.sohu.com', icon: '📺' },
    { name: '云栖社区', url: 'https://yq.aliyun.com', icon: '☁️' },
    { name: '脚本之家', url: 'https://www.jb51.net', icon: '🛠️' },
    { name: 'CSDN', url: 'https://www.csdn.net', icon: '📝' },
    { name: 'JavaGuide', url: 'https://snailclimb.top/JavaGuide', icon: '📖' },
    { name: 'Java程序核心知识', url: 'https://github.com/Snailclimb/JavaGuide', icon: '☕' },
    { name: 'VMware虚拟网卡', url: 'https://blog.csdn.net/czg13548930186/article/details/77099377', icon: '🖥️' },
    { name: '中国大学MOOC', url: 'https://www.icourse163.org', icon: '🎓' },
    { name: 'Apache ECharts', url: 'https://www.echartsjs.com/zh/index.html', icon: '📊' },
    { name: 'POI操作Excel', url: 'https://www.cnblogs.com/gdwkong/p/8669220.html', icon: '📊' },
    { name: '弹幕特效代码', url: 'https://www.17sucai.com/pins/tag/11535.html', icon: '✨' },
    { name: 'Edraw MindMaster', url: 'https://www.edrawsoft.com/en/mindmaster', icon: '🗺️' },
    { name: 'Java EE 6教程', url: 'https://docs.oracle.com/javaee/6/tutorial/doc', icon: '📕' },
    { name: 'Java', url: 'https://cloud.tencent.com/developer/article/1146268', icon: '☕' },
    { name: 'VMware', url: 'https://www.vmware.com/cn.html', icon: '🖥️' },
    { name: '牛耳', url: 'http://www.newer2001.com', icon: '🎯' },
    { name: 'IDEA破解', url: 'https://my.oschina.net/githubhty/blog/2245788', icon: '💡' },
    { name: 'IDEA第三方软件', url: 'https://confluence.jetbrains.com/display/IDEADEV', icon: '📦' },
    { name: '传智播客', url: 'https://www.imooc.com/article/288330', icon: '🎓' },
    { name: 'OSCHINA', url: 'https://www.oschina.net', icon: '🔧' },
    { name: 'sun拼音翻页', url: 'http://blog.chinaunix.net/uid-29485627-id-4363538.html', icon: '📝' },
    { name: '学信网', url: 'https://www.chsi.com.cn', icon: '🎓' },
    { name: 'JavaGuide GitHub', url: 'https://github.com/Snailclimb/JavaGuide', icon: '🐙' },
    { name: '黑马程序员', url: 'http://www.itheima.com', icon: '🐴' },
    { name: '搜狗输入法', url: 'https://pinyin.sogou.com/linux/help.php', icon: '🔤' },
    { name: '小米', url: 'https://account.xiaomi.com/pass/serviceLogin', icon: '📱' },
    { name: '小米商城', url: 'https://www.mi.com/index.html', icon: '📱' },
    { name: '后盾人', url: 'https://www.houdunren.com', icon: '🛡️' },
    { name: 'C++资源', url: 'https://github.com/AnkerLeng/Cpp-0-1-Resource', icon: '⚙️' },
    { name: '传智视频库', url: 'http://yun.itheima.com/?bili', icon: '🎬' },
    { name: 'Gmail', url: 'https://mail.google.com/mail/u/0/#inbox', icon: '✉️' },
    { name: 'Microsoft账户', url: 'https://account.microsoft.com', icon: '🪟' },
    { name: '用户脚本', url: 'https://greasyfork.org/zh-CN/scripts', icon: '📜' },
    { name: 'JetBrains', url: 'https://www.jetbrains.com', icon: '⚙️' },
    { name: 'MDN文档', url: 'https://developer.mozilla.org/zh-CN', icon: '🦖' },
    { name: 'SegmentFault', url: 'https://segmentfault.com', icon: '💡' },
    { name: 'Stack Overflow', url: 'https://stackoverflow.com', icon: '📚' },
    { name: '力扣', url: 'https://leetcode-cn.com', icon: '🏆' },
    { name: '牛客网', url: 'https://www.nowcoder.com', icon: '🎯' }
  ]
})

const folderData = {
  smallBar: selectedFolder.value,
  tools: {
    id: 'tools',
    name: '工具',
    items: [
      { name: '分隔符工具', url: 'https://separator.mayastudios.com/index.php?t=horz', icon: '➗' },
      { name: '多标签搜索', url: 'https://www.runningcheese.com/multi-search', icon: '🔍' },
      { name: '边栏搜索', url: 'https://www.runningcheese.com/sidebar-search', icon: '🔍' }
    ]
  },
  web: {
    id: 'web',
    name: '网页',
    items: [
      { name: 'Windows 12 网页版', url: 'http://p.xiaodu0.com/desktop.html', icon: '🖥️' },
      { name: '小鹅通学员版', url: 'https://study.xiaoe-tech.com/t_l/learnIndex', icon: '📚' },
      { name: 'RunningCheese', url: 'https://www.runningcheese.com/bookmarklets', icon: '🧀' }
    ]
  },
  reading: {
    id: 'reading',
    name: '阅读',
    items: [
      { name: '破局行动', url: 'https://aipoju.com/action', icon: '🎯' },
      { name: 'CSDN', url: 'https://www.csdn.net', icon: '📝' }
    ]
  },
  text: {
    id: 'text',
    name: '文字',
    items: [
      { name: '分隔符', url: 'https://separator.mayastudios.com/index.php?t=horz#', icon: '─' }
    ]
  },
  search: {
    id: 'search',
    name: '搜索',
    items: [
      { name: '多标签搜索', url: 'https://www.runningcheese.com/multi-search', icon: '🔍' }
    ]
  },
  searchEngines: {
    id: 'searchEngines',
    name: '搜索引擎',
    items: [
      { name: 'Google', url: 'https://www.google.com', icon: '🔍' },
      { name: '百度', url: 'https://www.baidu.com', icon: '🐻' }
    ]
  },
  sidebarSearch: {
    id: 'sidebarSearch',
    name: '边栏搜索',
    items: [
      { name: '边栏搜索', url: 'https://www.runningcheese.com/sidebar-search', icon: '🔍' }
    ]
  },
  links: {
    id: 'links',
    name: '链接',
    items: [
      { name: 'Excalidraw', url: 'https://excalidraw.com', icon: '✏️' },
      { name: 'Adobe', url: 'https://www.adobe.com', icon: '🎨' }
    ]
  },
  images: {
    id: 'images',
    name: '图片',
    items: []
  },
  design: {
    id: 'design',
    name: '设计',
    items: [
      { name: 'Excalidraw', url: 'https://excalidraw.com', icon: '✏️' },
      { name: 'ECharts', url: 'https://www.echartsjs.com', icon: '📊' },
      { name: '弹幕特效', url: 'https://www.17sucai.com', icon: '✨' },
      { name: '思维导图', url: 'https://www.edrawsoft.com', icon: '🗺️' }
    ]
  },
  development: {
    id: 'development',
    name: '开发',
    items: [
      { name: 'CSDN', url: 'https://www.csdn.net', icon: '📝' },
      { name: 'GitHub', url: 'https://github.com', icon: '🐙' },
      { name: '博客园', url: 'https://www.cnblogs.com', icon: '📖' },
      { name: '脚本之家', url: 'https://www.jb51.net', icon: '🛠️' },
      { name: '开源中国', url: 'https://www.oschina.net', icon: '🔧' }
    ]
  },
  imported: {
    id: 'imported',
    name: '已导入',
    items: []
  }
}

const toggleFolder = (key) => {
  expandedFolders.value[key] = !expandedFolders.value[key]
}

const selectFolder = (folderId) => {
  selectedFolder.value = folderData[folderId] || folderData.smallBar
}
</script>

<style scoped>
.bookmarks {
  background-color: var(--bg-dark);
  padding: 60px 0;
}

.section-title {
  font-size: 2rem;
  font-weight: 700;
  margin-bottom: 0.5rem;
  color: var(--text-dark);
  text-align: center;
  text-shadow: var(--glow-text);
  letter-spacing: 1px;
}

.section-subtitle {
  font-size: 0.95rem;
  color: var(--text-light);
  text-align: center;
  margin-bottom: 2rem;
  max-width: 500px;
  margin-left: auto;
  margin-right: auto;
}

.bookmarks-wrapper {
  max-width: 1000px;
  margin: 0 auto;
  display: grid;
  grid-template-columns: 250px 1fr;
  gap: 0;
  background: rgba(10, 14, 39, 0.9);
  border-radius: 8px;
  overflow: hidden;
  border: 1px solid rgba(0, 240, 255, 0.1);
}

/* 左侧树形结构 */
.bookmarks-tree {
  background: rgba(5, 10, 30, 0.9);
  border-right: 1px solid rgba(0, 240, 255, 0.08);
}

.tree-content {
  max-height: 700px;
  overflow-y: auto;
  padding: 0.5rem 0;
}

.tree-content::-webkit-scrollbar {
  width: 6px;
}

.tree-content::-webkit-scrollbar-track {
  background: rgba(0, 0, 0, 0.2);
}

.tree-content::-webkit-scrollbar-thumb {
  background: rgba(0, 240, 255, 0.2);
  border-radius: 3px;
}

.tree-item {
  user-select: none;
}

.tree-node {
  display: flex;
  align-items: center;
  gap: 0.3rem;
  padding: 0.35rem 0.6rem;
  cursor: pointer;
  transition: all 0.15s ease;
  font-size: 0.8rem;
}

.tree-node:hover {
  background: rgba(0, 240, 255, 0.06);
}

.tree-node.selected {
  background: rgba(0, 240, 255, 0.12);
}

.tree-node.selected .tree-label {
  color: var(--primary-color);
}

.tree-chevron {
  font-size: 0.6rem;
  color: var(--text-light);
  width: 8px;
}

.tree-icon {
  font-size: 0.85rem;
  flex-shrink: 0;
  width: 14px;
}

.tree-label {
  flex: 1;
  font-size: 0.8rem;
  font-weight: 500;
  color: var(--text-dark);
}

.tree-children {
  margin-left: 0.8rem;
}

/* 右侧详细内容 */
.bookmarks-detail {
  padding: 1rem;
  background: rgba(5, 10, 30, 0.7);
}

.detail-header {
  margin-bottom: 0.8rem;
  padding-bottom: 0.5rem;
  border-bottom: 1px solid rgba(0, 240, 255, 0.08);
}

.detail-title {
  font-size: 0.9rem;
  font-weight: 600;
  color: var(--text-dark);
  margin: 0;
}

.detail-content {
  display: flex;
  flex-direction: column;
  gap: 0.3rem;
  max-height: 650px;
  overflow-y: auto;
}

.detail-content::-webkit-scrollbar {
  width: 6px;
}

.detail-content::-webkit-scrollbar-track {
  background: rgba(0, 0, 0, 0.1);
}

.detail-content::-webkit-scrollbar-thumb {
  background: rgba(0, 240, 255, 0.2);
  border-radius: 3px;
}

.detail-item {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.4rem 0.6rem;
  background: rgba(10, 14, 39, 0.3);
  border-radius: 4px;
  border: 1px solid rgba(0, 240, 255, 0.03);
  transition: all 0.2s ease;
}

.detail-item:hover {
  background: rgba(0, 240, 255, 0.06);
  border-color: rgba(0, 240, 255, 0.15);
}

.detail-icon {
  font-size: 1rem;
  width: 24px;
  height: 24px;
  display: flex;
  align-items: center;
  justify-content: center;
  flex-shrink: 0;
}

.detail-info {
  flex: 1;
  min-width: 0;
}

.detail-name {
  display: block;
  font-size: 0.8rem;
  font-weight: 500;
  color: var(--text-dark);
  text-decoration: none;
  margin-bottom: 0.1rem;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
}

.detail-name:hover {
  color: var(--primary-color);
}

.detail-url {
  font-size: 0.65rem;
  color: var(--text-light);
  display: block;
  white-space: nowrap;
  overflow: hidden;
  text-overflow: ellipsis;
  opacity: 0.5;
}

@media (max-width: 968px) {
  .bookmarks-wrapper {
    grid-template-columns: 1fr;
    max-width: 600px;
  }

  .bookmarks-tree {
    border-right: none;
    border-bottom: 1px solid rgba(0, 240, 255, 0.08);
  }

  .tree-content {
    max-height: 300px;
  }
}
</style>
