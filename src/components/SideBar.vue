<script setup>
// 定义props
const props = defineProps({
  categories: Array,
  activeCategory: Number
})

// 定义emits
const emit = defineEmits(['change-category'])

// 切换分类
const selectCategory = (categoryId) => {
  emit('change-category', categoryId)
}
</script>

<template>
  <aside class="sidebar">
    <div class="categories">
      <h3 class="sidebar-title">网站分类</h3>
      <ul class="category-list">
        <li 
          v-for="category in categories" 
          :key="category.id"
          :class="{ active: category.id === activeCategory }"
          @click="selectCategory(category.id)"
        >
          {{ category.name }}
        </li>
      </ul>
    </div>
  </aside>
</template>

<style scoped>
.sidebar {
  width: 200px;
  background-color: rgba(22, 22, 22, 0.7);
  border-right: none;
  padding: 1.5rem 0.75rem;
  min-height: auto;
  position: relative;
  z-index: 10;
  border-radius: 16px;
  border: 1px solid rgba(114, 137, 218, 0.1);
  flex-shrink: 0;
  box-shadow: var(--card-shadow);
  backdrop-filter: blur(10px);
  height: auto;
  overflow-y: visible;
}

.sidebar-title {
  padding: 0 1.25rem;
  font-size: 0.9rem;
  color: var(--text-secondary);
  margin-bottom: 1.5rem;
  letter-spacing: 0.05em;
  text-transform: uppercase;
  font-weight: 600;
  opacity: 0.8;
  position: relative;
}

.sidebar-title::after {
  content: '';
  position: absolute;
  bottom: -8px;
  left: 1.25rem;
  width: 30px;
  height: 2px;
  background: linear-gradient(90deg, var(--accent-color), transparent);
  border-radius: 3px;
}

.category-list {
  list-style: none;
  padding: 0 0.5rem;
  max-height: calc(100vh - 220px);
  overflow-y: auto;
}

.category-list li {
  padding: 0.9rem 1.25rem;
  cursor: pointer;
  transition: all 0.3s ease;
  color: var(--text-secondary);
  font-size: 0.95rem;
  border-left: none;
  margin-bottom: 6px;
  display: flex;
  align-items: center;
  border-radius: 10px;
  position: relative;
  overflow: hidden;
}

.category-list li::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 0;
  height: 100%;
  background: linear-gradient(90deg, rgba(114, 137, 218, 0.1), transparent);
  transition: width 0.3s ease;
  z-index: -1;
}

.category-list li:hover {
  background-color: var(--bg-hover);
  color: var(--text-primary);
  transform: translateX(5px);
}

.category-list li:hover::before {
  width: 100%;
}

.category-list li.active {
  background: linear-gradient(90deg, rgba(114, 137, 218, 0.15), rgba(30, 30, 30, 0.5));
  border-left: none;
  color: var(--accent-color);
  font-weight: 500;
  box-shadow: 0 3px 8px rgba(0, 0, 0, 0.1);
  transform: translateX(5px);
}

.category-list li.active::after {
  content: '';
  position: absolute;
  left: 0;
  top: 50%;
  transform: translateY(-50%);
  width: 3px;
  height: 60%;
  background: var(--accent-color);
  border-radius: 0 3px 3px 0;
}

@media (max-width: 1200px) {
  .sidebar {
    width: 180px;
    padding: 1.5rem 0.5rem;
  }
  
  .sidebar-title {
    padding: 0 1.25rem;
    margin-bottom: 1.25rem;
  }
  
  .category-list li {
    padding: 0.75rem 1.25rem;
  }
}

@media (max-width: 768px) {
  .sidebar {
    width: 100%;
    min-height: unset;
    border-right: none;
    border-bottom: none;
    padding: 1rem 0.75rem;
    position: relative;
    height: auto;
    overflow-x: auto;
    z-index: 9;
    border-radius: 16px;
    margin-bottom: 15px;
  }
  
  .sidebar-title {
    padding: 0 1.25rem;
    margin-bottom: 1rem;
    font-size: 0.9rem;
  }
  
  .sidebar-title::after {
    left: 1.25rem;
    width: 25px;
    height: 2px;
    bottom: -6px;
  }
  
  .category-list {
    display: flex;
    overflow-x: auto;
    padding: 0.25rem;
    -webkit-overflow-scrolling: touch;
    scroll-snap-type: x mandatory;
    max-height: none;
  }
  
  .category-list li {
    padding: 0.7rem 1.25rem;
    white-space: nowrap;
    flex-shrink: 0;
    margin-right: 0.75rem;
    border-radius: 10px;
    border-left: none;
    scroll-snap-align: start;
    font-size: 0.9rem;
    margin-bottom: 0;
    background: rgba(30, 30, 30, 0.4);
    border: 1px solid rgba(114, 137, 218, 0.08);
  }
  
  .category-list li:hover {
    transform: translateY(-3px);
  }
  
  .category-list li.active {
    background: linear-gradient(135deg, rgba(114, 137, 218, 0.2), rgba(50, 50, 50, 0.4));
    transform: translateY(-3px);
  }
  
  .category-list li.active::after {
    left: 50%;
    top: auto;
    bottom: 0;
    transform: translateX(-50%);
    width: 60%;
    height: 2px;
    border-radius: 2px 2px 0 0;
  }
  
  .category-list li:last-child {
    margin-right: 0.5rem;
  }
}

@media (max-width: 480px) {
  .sidebar {
    top: 120px; /* 手机小屏幕顶部导航栏调整 */
  }
  
  .sidebar-title {
    font-size: 0.8rem;
  }
  
  .category-list li {
    font-size: 0.9rem;
    padding: 0.4rem 0.8rem;
  }
}
</style> 