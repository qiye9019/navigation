<script setup>
import { ref } from 'vue'

const searchQuery = ref('')

const handleSearch = () => {
  // 将在二期实现搜索功能
  console.log('搜索:', searchQuery.value)
}
</script>

<template>
  <header class="top-bar">
    <div class="logo">
      <h1>我的导航站</h1>
    </div>
    <div class="search-bar">
      <input 
        type="text" 
        v-model="searchQuery" 
        placeholder="搜索网站..." 
        @keyup.enter="handleSearch"
      />
      <button @click="handleSearch">搜索</button>
    </div>
    <div class="user-actions">
      <button class="settings-btn">
        <span class="icon">⚙️</span>
      </button>
    </div>
  </header>
</template>

<style scoped>
.top-bar {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 1rem 40px;
  background-color: rgba(22, 22, 22, 0.8);
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.2);
  position: relative;
  z-index: 100;
  backdrop-filter: blur(15px);
  border-bottom: 1px solid rgba(114, 137, 218, 0.1);
  width: 100%;
}

.logo h1 {
  font-size: 1.75rem;
  font-weight: 700;
  color: var(--text-primary);
  margin: 0;
  background: linear-gradient(90deg, var(--accent-color), #9f7aea);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
  letter-spacing: -0.5px;
  position: relative;
  display: inline-block;
  text-shadow: 0 5px 15px rgba(114, 137, 218, 0.3);
  white-space: nowrap;
}

.logo h1::after {
  content: '';
  position: absolute;
  bottom: -5px;
  left: 0;
  width: 30px;
  height: 3px;
  background: linear-gradient(90deg, var(--accent-color), #9f7aea);
  border-radius: 3px;
}

.search-bar {
  display: flex;
  flex: 1;
  max-width: 500px;
  margin: 0 3rem;
  position: relative;
}

.search-bar input {
  flex: 1;
  padding: 0.9rem 1.25rem;
  border: 1px solid rgba(114, 137, 218, 0.2);
  border-radius: 12px;
  font-size: 1rem;
  background-color: rgba(25, 25, 25, 0.6);
  color: var(--text-primary);
  width: 100%;
  backdrop-filter: blur(5px);
  box-shadow: inset 0 2px 5px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
}

.search-bar input:focus {
  outline: none;
  border-color: var(--accent-color);
  box-shadow: 0 0 0 2px rgba(114, 137, 218, 0.25), inset 0 2px 5px rgba(0, 0, 0, 0.1);
}

.search-bar input::placeholder {
  color: var(--text-secondary);
  opacity: 0.7;
}

.search-bar button {
  position: absolute;
  right: 0;
  top: 0;
  height: 100%;
  padding: 0 1.5rem;
  background: linear-gradient(90deg, var(--accent-color), #9f7aea);
  color: white;
  border: none;
  border-radius: 0 12px 12px 0;
  cursor: pointer;
  font-weight: 500;
  font-size: 1rem;
  transition: all 0.3s ease;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.search-bar button:hover {
  background: linear-gradient(90deg, #6677cc, #8f63d8);
  box-shadow: 0 4px 10px rgba(0, 0, 0, 0.2);
  transform: translateY(-1px);
}

.user-actions button {
  background: rgba(30, 30, 30, 0.5);
  border: 1px solid rgba(114, 137, 218, 0.1);
  font-size: 1.5rem;
  cursor: pointer;
  opacity: 0.8;
  transition: all 0.3s ease;
  color: var(--text-primary);
  width: 48px;
  height: 48px;
  border-radius: 50%;
  display: flex;
  align-items: center;
  justify-content: center;
  backdrop-filter: blur(5px);
  box-shadow: 0 3px 10px rgba(0, 0, 0, 0.1);
}

.user-actions button:hover {
  opacity: 1;
  background-color: rgba(114, 137, 218, 0.15);
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
}

@media (max-width: 1200px) {
  .top-bar {
    padding: 1rem 30px;
  }
  
  .search-bar {
    margin: 0 2rem;
  }
}

@media (max-width: 768px) {
  .top-bar {
    flex-direction: column;
    padding: 1rem 20px;
    gap: 1rem;
  }
  
  .logo {
    margin-bottom: 0;
  }
  
  .search-bar {
    width: 100%;
    margin: 0;
    max-width: none;
  }
  
  .logo h1::after {
    bottom: -4px;
    left: 50%;
    transform: translateX(-50%);
    width: 40px;
  }
}

@media (max-width: 480px) {
  .top-bar {
    padding: 1rem 15px;
  }
  
  .user-actions {
    position: absolute;
    right: 15px;
    top: 1rem;
  }
  
  .user-actions button {
    width: 40px;
    height: 40px;
    font-size: 1.3rem;
  }
  
  .logo h1 {
    font-size: 1.5rem;
    margin: 0 auto;
  }
  
  .search-bar input {
    padding: 0.75rem 1rem;
    border-radius: 10px;
  }
  
  .search-bar button {
    padding: 0 1.25rem;
    border-radius: 0 10px 10px 0;
  }
}
</style> 