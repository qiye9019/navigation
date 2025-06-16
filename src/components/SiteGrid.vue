<script setup>
import { ref, computed } from 'vue'

const props = defineProps({
  categoryId: Number
})

// 模拟网站数据，实际应用中可以从localStorage读取或API获取
const websites = ref([
  { 
    id: 1, 
    name: '百度',
    url: 'https://www.baidu.com',
    description: '中文搜索引擎',
    icon: 'https://www.baidu.com/favicon.ico',
    categoryId: 1
  },
  { 
    id: 2, 
    name: '谷歌',
    url: 'https://www.google.com',
    description: '全球最大的搜索引擎',
    icon: 'https://www.google.com/favicon.ico',
    categoryId: 1
  },
  { 
    id: 9, 
    name: '必应',
    url: 'https://cn.bing.com/',
    description: '微软旗下的搜索引擎',
    icon: 'https://cn.bing.com/favicon.ico',
    categoryId: 1
  },
  { 
    id: 10, 
    name: '纳米搜索',
    url: 'https://cn.bing.com/',
    description: '基于必应的搜索服务',
    icon: 'https://cn.bing.com/favicon.ico',
    categoryId: 1
  },
  { 
    id: 11, 
    name: '搜狗搜索',
    url: 'https://www.sogou.com/',
    description: '腾讯旗下的搜索引擎',
    icon: 'https://www.sogou.com/favicon.ico',
    categoryId: 1
  },
  { 
    id: 12, 
    name: '360搜索',
    url: 'https://www.so.com/',
    description: '360旗下的搜索引擎',
    icon: 'https://www.so.com/favicon.ico',
    categoryId: 1
  },
  { 
    id: 3, 
    name: 'GitHub',
    url: 'https://github.com',
    description: '开源代码托管平台',
    icon: 'https://github.com/favicon.ico',
    categoryId: 4
  },
  { 
    id: 4, 
    name: 'Bilibili',
    url: 'https://www.bilibili.com',
    description: '中国年轻人喜欢的视频弹幕网站',
    icon: 'https://www.bilibili.com/favicon.ico',
    categoryId: 3
  },
  { 
    id: 18, 
    name: '腾讯视频',
    url: 'https://v.qq.com',
    description: '腾讯视频是中国领先的在线视频媒体平台',
    icon: 'https://v.qq.com/favicon.ico',
    categoryId: 3
  },
  { 
    id: 19, 
    name: '爱奇艺',
    url: 'https://www.iqiyi.com',
    description: '中国领先的在线视频网站',
    icon: 'https://www.iqiyi.com/favicon.ico',
    categoryId: 3
  },
  { 
    id: 20, 
    name: '网易云音乐',
    url: 'https://music.163.com',
    description: '网易云音乐是一款专注于发现与分享的音乐产品',
    icon: 'https://music.163.com/favicon.ico',
    categoryId: 3
  },
  { 
    id: 21, 
    name: 'QQ音乐',
    url: 'https://y.qq.com',
    description: '腾讯旗下音乐平台，提供海量音乐在线试听',
    icon: 'https://y.qq.com/favicon.ico',
    categoryId: 3
  },
  { 
    id: 22, 
    name: '斗鱼直播',
    url: 'https://www.douyu.com',
    description: '中国领先的直播平台，提供游戏、娱乐等直播内容',
    icon: 'https://www.douyu.com/favicon.ico',
    categoryId: 3
  },
  { 
    id: 23, 
    name: '虎牙直播',
    url: 'https://www.huya.com',
    description: '中国领先的游戏直播平台',
    icon: 'https://www.huya.com/favicon.ico',
    categoryId: 3
  },
  { 
    id: 24, 
    name: 'Steam',
    url: 'https://store.steampowered.com',
    description: '全球最大的数字游戏发行平台',
    icon: 'https://store.steampowered.com/favicon.ico',
    categoryId: 3
  },
  { 
    id: 25, 
    name: 'Epic Games',
    url: 'https://store.epicgames.com',
    description: 'Epic Games Store，提供优质游戏和免费游戏',
    icon: 'https://store.epicgames.com/favicon.ico',
    categoryId: 3
  },
  { 
    id: 26, 
    name: '优酷视频',
    url: 'https://www.youku.com',
    description: '中国领先的视频服务平台，提供海量优质视频',
    icon: 'https://www.youku.com/favicon.ico',
    categoryId: 3
  },
  { 
    id: 27, 
    name: '芒果TV',
    url: 'https://www.mgtv.com',
    description: '湖南广电旗下视频网站，提供优质综艺和影视内容',
    icon: 'https://www.mgtv.com/favicon.ico',
    categoryId: 3
  },
  { 
    id: 28, 
    name: '酷狗音乐',
    url: 'https://www.kugou.com',
    description: '中国领先的数字音乐交互服务提供商',
    icon: 'https://www.kugou.com/favicon.ico',
    categoryId: 3
  },
  { 
    id: 29, 
    name: '抖音',
    url: 'https://www.douyin.com',
    description: '字节跳动旗下短视频平台，记录美好生活',
    icon: 'https://www.douyin.com/favicon.ico',
    categoryId: 3
  },
  { 
    id: 30, 
    name: '快手',
    url: 'https://www.kuaishou.com',
    description: '中国领先的短视频社区，记录和分享生活',
    icon: 'https://www.kuaishou.com/favicon.ico',
    categoryId: 3
  },
  { 
    id: 5, 
    name: '知乎',
    url: 'https://www.zhihu.com',
    description: '中文问答社区',
    icon: 'https://www.zhihu.com/favicon.ico',
    categoryId: 5
  },
  { 
    id: 6, 
    name: 'MDN Web Docs',
    url: 'https://developer.mozilla.org',
    description: 'Web开发者文档',
    icon: 'https://developer.mozilla.org/favicon.ico',
    categoryId: 2
  },
  { 
    id: 13, 
    name: '中国大学MOOC',
    url: 'https://www.icourse163.org/',
    description: '中国大学MOOC(慕课) 是爱课程网携手网易云课堂打造的在线学习平台',
    icon: 'https://www.icourse163.org/favicon.ico',
    categoryId: 2
  },
  { 
    id: 14, 
    name: '慕课网',
    url: 'https://www.imooc.com/',
    description: '慕课网是垂直的互联网IT技能免费学习网站',
    icon: 'https://www.imooc.com/favicon.ico',
    categoryId: 2
  },
  { 
    id: 15, 
    name: '我要自学网',
    url: 'https://www.51zxw.net/',
    description: '我要自学网提供全方位软件学习，有3D教程，平面教程，多媒体制作教程，办公信息化教程，机械设计教程，网站制作教程，电脑培训',
    icon: 'https://www.51zxw.net/favicon.ico',
    categoryId: 2
  },
  { 
    id: 16, 
    name: '网易云课堂',
    url: 'https://study.163.com/',
    description: '网易云课堂，是网易公司打造的在线实用技能学习平台',
    icon: 'https://study.163.com/favicon.ico',
    categoryId: 2
  },
  { 
    id: 17, 
    name: '网易公开课',
    url: 'https://open.163.com/',
    description: '网易公开课，打造最全的免费课程平台',
    icon: 'https://open.163.com/favicon.ico',
    categoryId: 2
  },
  { 
    id: 7, 
    name: 'YouTube',
    url: 'https://www.youtube.com',
    description: '全球最大的视频分享平台',
    icon: 'https://www.youtube.com/favicon.ico',
    categoryId: 3
  },
  { 
    id: 8, 
    name: 'Stack Overflow',
    url: 'https://stackoverflow.com',
    description: '程序员问答社区',
    icon: 'https://stackoverflow.com/favicon.ico',
    categoryId: 4
  }
])

// 根据当前分类筛选网站
const filteredWebsites = computed(() => {
  return websites.value.filter(site => site.categoryId === props.categoryId)
})

// 打开网站
const openWebsite = (url) => {
  window.open(url, '_blank')
}
</script>

<template>
  <main class="site-grid">
    <div v-if="filteredWebsites.length > 0" class="grid" :data-category="categoryId">
      <div 
        v-for="site in filteredWebsites" 
        :key="site.id"
        class="site-card"
        @click="openWebsite(site.url)"
      >
        <div class="site-icon">
          <img :src="site.icon" :alt="site.name" />
        </div>
        <div class="site-info">
          <h3 class="site-name">{{ site.name }}</h3>
          <p class="site-description">{{ site.description }}</p>
        </div>
      </div>
    </div>
    <div v-else class="empty-state">
      <p>当前分类没有网站</p>
      <button class="add-site-btn">添加网站</button>
    </div>
  </main>
</template>

<style scoped>
.site-grid {
  flex: 1;
  padding: 2rem;
  background-color: rgba(22, 22, 22, 0.7);
  overflow: visible;
  min-height: 100%;
  border-radius: 20px;
  border: 1px solid rgba(114, 137, 218, 0.1);
  box-shadow: var(--card-shadow);
  backdrop-filter: blur(10px);
  position: relative;
  z-index: 5;
  width: 100%;
  max-width: 1800px;
  margin: 0 auto;
}

.grid {
  display: flex;
  flex-wrap: wrap;
  gap: 1.5rem;
  padding-top: 10px;
  width: 100%;
  justify-content: flex-start;
}

.site-card {
  flex: 0 0 auto;
  width: 200px;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background: linear-gradient(145deg, rgba(35, 35, 35, 0.9), rgba(25, 25, 25, 0.9));
  border-radius: 16px;
  padding: 1.5rem;
  box-shadow: 0 6px 15px rgba(0, 0, 0, 0.15);
  cursor: pointer;
  transition: all 0.4s cubic-bezier(0.175, 0.885, 0.32, 1.275);
  border: 1px solid rgba(114, 137, 218, 0.15);
  position: relative;
  overflow: hidden;
  min-height: 150px;
}

.site-card::before {
  content: '';
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background: 
    radial-gradient(
      circle at top right,
      rgba(114, 137, 218, 0.12),
      transparent 70%
    );
  opacity: 0;
  transition: opacity 0.4s ease;
}

.site-card:hover {
  transform: translateY(-8px) scale(1.03);
  box-shadow: 0 12px 25px rgba(0, 0, 0, 0.25);
  border-color: var(--accent-color);
}

.site-card:hover::before {
  opacity: 1;
}

.site-icon {
  width: 48px;
  height: 48px;
  margin-bottom: 1.25rem;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(40, 40, 40, 0.7);
  border-radius: 12px;
  padding: 0.75rem;
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
  border: 1px solid rgba(255, 255, 255, 0.05);
  transition: transform 0.5s ease, box-shadow 0.5s ease;
}

.site-card:hover .site-icon {
  transform: scale(1.1) translateY(-3px);
  box-shadow: 0 8px 15px rgba(114, 137, 218, 0.2);
  border-color: rgba(114, 137, 218, 0.3);
}

.site-icon img {
  max-width: 100%;
  max-height: 100%;
  border-radius: 4px;
  object-fit: contain;
  filter: drop-shadow(0 1px 2px rgba(0, 0, 0, 0.1));
}

.site-info {
  text-align: center;
  width: 100%;
  z-index: 1;
}

.site-name {
  font-size: 1rem;
  margin-bottom: 0.5rem;
  color: var(--text-primary);
  font-weight: 600;
  letter-spacing: -0.5px;
  text-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
}

.site-description {
  font-size: 0.85rem;
  color: var(--text-secondary);
  overflow: hidden;
  text-overflow: ellipsis;
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  line-height: 1.4;
}

.empty-state {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  height: 300px;
  color: var(--text-secondary);
}

.add-site-btn {
  margin-top: 1.5rem;
  padding: 0.75rem 1.5rem;
  background: linear-gradient(135deg, var(--accent-color), #9f7aea);
  color: white;
  border: none;
  border-radius: 8px;
  cursor: pointer;
  transition: all 0.3s ease;
  font-weight: 500;
  font-size: 0.9rem;
  box-shadow: 0 4px 8px rgba(114, 137, 218, 0.3);
  letter-spacing: 0.5px;
}

.add-site-btn:hover {
  transform: translateY(-3px);
  box-shadow: 0 6px 12px rgba(114, 137, 218, 0.5);
}

@media (min-width: 1600px) {
  .site-card {
    width: 220px;
  }
}

@media (max-width: 1400px) {
  .site-card {
    width: 190px;
  }
}

@media (max-width: 1200px) {
  .site-card {
    width: 180px;
    padding: 1.25rem;
    min-height: 140px;
  }
}

@media (max-width: 768px) {
  .site-grid {
    padding: 1.5rem;
  }
  
  .grid {
    gap: 1rem;
  }
  
  .site-card {
    width: 160px;
    padding: 1.25rem;
    min-height: 130px;
  }
}

@media (max-width: 480px) {
  .site-grid {
    padding: 1rem;
  }
  
  .grid {
    gap: 1rem;
    padding-top: 5px;
  }
  
  .site-card {
    width: 140px;
    padding: 1rem;
    min-height: 120px;
  }
}
</style> 