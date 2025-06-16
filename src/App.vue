<script setup>
// 导入组件
import { ref } from 'vue'
import SideBar from './components/SideBar.vue'
import TopBar from './components/TopBar.vue'
import SiteGrid from './components/SiteGrid.vue'

// 网站数据
const categories = ref([
  { id: 1, name: '常用工具' },
  { id: 2, name: '学习资源' },
  { id: 3, name: '娱乐网站' },
  { id: 4, name: '开发工具' },
  { id: 5, name: '社交媒体' }
])

const activeCategory = ref(1)

// 切换分类
const changeCategory = (categoryId) => {
  activeCategory.value = categoryId
}
</script>

<template>
  <div class="app-container">
    <!-- 顶部区域 -->
    <TopBar />
    
    <div class="main-content">
      <!-- 左侧边栏 -->
      <SideBar 
        :categories="categories" 
        :activeCategory="activeCategory" 
        @change-category="changeCategory" 
      />
      
      <!-- 主内容区 -->
      <SiteGrid :categoryId="activeCategory" />
    </div>
    
    <!-- 底部区域 -->
    <footer class="footer">
      <p>个人导航站 © {{ new Date().getFullYear() }}</p>
    </footer>
  </div>
</template>

<style>
:root {
  /* 暗色主题变量 */
  --bg-primary: #121212;
  --bg-secondary: #1e1e1e;
  --bg-hover: #2a2a2a;
  --text-primary: #e1e1e1;
  --text-secondary: #a0a0a0;
  --accent-color: #7289da;
  --accent-hover: #5f73bc;
  --border-color: #333333;
  --card-shadow: 0 8px 16px rgba(0, 0, 0, 0.2);
}

* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

html {
  height: 100%;
  width: 100%;
  background-color: var(--bg-primary);
  color: var(--text-primary);
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  line-height: 1.6;
  overflow-x: hidden;
}

body {
  height: 100%;
  width: 100%;
  background: linear-gradient(135deg, #121212 0%, #1a1a1a 100%);
  overflow-x: hidden;
  position: relative;
}

a {
  color: var(--accent-color);
  text-decoration: none;
}

button {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}

.app-container {
  display: flex;
  flex-direction: column;
  min-height: 100vh;
  width: 100%;
}

.main-content {
  display: flex;
  flex: 1;
  gap: 20px;
  position: relative;
  width: 100%;
  max-width: 1600px;
  margin: 0 auto;
  padding: 20px 40px;
  height: 100%;
}

.footer {
  text-align: center;
  padding: 1.5rem 0;
  background-color: rgba(30, 30, 30, 0.7);
  border-top: 1px solid var(--border-color);
  margin-top: 30px;
  color: var(--text-secondary);
  font-size: 0.9rem;
  border-radius: 0;
  backdrop-filter: blur(10px);
  position: relative;
  z-index: 10;
  pointer-events: none;
}

/* 自定义滚动条样式 */
::-webkit-scrollbar {
  width: 8px;
  height: 8px;
}

::-webkit-scrollbar-track {
  background: var(--bg-primary);
}

::-webkit-scrollbar-thumb {
  background-color: var(--border-color);
  border-radius: 10px;
  border: 2px solid var(--bg-primary);
}

::-webkit-scrollbar-thumb:hover {
  background-color: var(--accent-color);
}

/* 背景装饰 */
.app-container::before {
  content: '';
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: 
    radial-gradient(circle at 10% 10%, rgba(114, 137, 218, 0.03), transparent 40%),
    radial-gradient(circle at 90% 90%, rgba(114, 137, 218, 0.03), transparent 40%);
  z-index: -1;
  pointer-events: none;
}

@media (max-width: 1200px) {
  .main-content {
    gap: 15px;
    padding: 20px 30px;
    max-width: 100%;
  }
}

@media (max-width: 768px) {
  .main-content {
    flex-direction: column;
    gap: 15px;
    padding: 20px;
    max-width: 100%;
  }
  
  .footer {
    padding: 1.25rem 0;
    margin-top: 20px;
  }
}

@media (max-width: 480px) {
  .main-content {
    gap: 10px;
    padding: 15px;
    max-width: 100%;
  }
  
  .footer {
    margin-top: 15px;
    font-size: 0.8rem;
    padding: 1rem 0;
  }
}
</style>
