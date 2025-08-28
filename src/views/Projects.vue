<template>
  <div class="projects">
    <!-- 页面标题 -->
    <section class="section-padding bg-apple-light-gray">
      <div class="container-max text-center">
        <h1 class="text-large font-bold text-apple-text mb-6">作品集</h1>
        <p class="text-xl text-apple-text-secondary max-w-3xl mx-auto">
          探索我的项目作品，每一个项目都凝聚着对技术的热爱和对用户体验的追求
        </p>
      </div>
    </section>

    <!-- 项目筛选 -->
    <section class="section-padding">
      <div class="container-max">
        <div class="flex flex-wrap justify-center gap-4 mb-12">
          <button 
            v-for="category in categories" 
            :key="category"
            @click="selectedCategory = category"
            class="px-6 py-3 rounded-full font-medium transition-all duration-300"
            :class="selectedCategory === category 
              ? 'bg-apple-blue text-white' 
              : 'bg-white text-apple-text border border-gray-200 hover:border-apple-blue hover:text-apple-blue'"
          >
            {{ category }}
          </button>
        </div>
        
        <!-- 项目网格 -->
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div 
            v-for="project in filteredProjects" 
            :key="project.id"
            :id="`project-${project.id}`"
            class="bg-white rounded-2xl overflow-hidden shadow-lg card-hover group"
          >
            <!-- 项目图片 -->
            <div class="relative overflow-hidden aspect-video bg-gradient-to-br from-apple-blue/10 to-purple-600/10">
              <div class="absolute inset-0 flex items-center justify-center">
                <div class="w-20 h-20 bg-white/80 rounded-2xl flex items-center justify-center">
                  <svg class="w-10 h-10 text-apple-blue" fill="currentColor" viewBox="0 0 24 24">
                    <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/>
                  </svg>
                </div>
              </div>
              <!-- 项目状态标签 -->
              <div class="absolute top-4 right-4">
                <span 
                  class="px-3 py-1 rounded-full text-xs font-medium"
                  :class="project.status === '已完成' ? 'bg-green-100 text-green-800' : 'bg-yellow-100 text-yellow-800'"
                >
                  {{ project.status }}
                </span>
              </div>
            </div>
            
            <!-- 项目信息 -->
            <div class="p-6">
              <h3 class="text-xl font-semibold text-apple-text mb-3 group-hover:text-apple-blue transition-colors">
                {{ project.name }}
              </h3>
              <p class="text-apple-text-secondary mb-4 line-clamp-3">
                {{ project.description }}
              </p>
              
              <!-- 技术标签 -->
              <div class="flex flex-wrap gap-2 mb-4">
                <span 
                  v-for="tech in project.technologies" 
                  :key="tech"
                  class="px-3 py-1 bg-apple-light-gray text-apple-text-secondary text-sm rounded-full"
                >
                  {{ tech }}
                </span>
              </div>
              
              <!-- 项目链接 -->
              <div class="flex gap-3">
                <a 
                  v-if="project.demoUrl"
                  :href="project.demoUrl" 
                  target="_blank"
                  class="flex-1 bg-apple-blue text-white text-center py-2 px-4 rounded-lg font-medium hover:bg-apple-dark-blue transition-colors"
                >
                  查看演示
                </a>
                <a 
                  v-if="project.githubUrl"
                  :href="project.githubUrl" 
                  target="_blank"
                  class="flex-1 border border-apple-blue text-apple-blue text-center py-2 px-4 rounded-lg font-medium hover:bg-apple-blue hover:text-white transition-colors"
                >
                  查看源码
                </a>
              </div>
            </div>
          </div>
        </div>
        
        <!-- 空状态 -->
        <div 
          v-if="filteredProjects.length === 0"
          class="text-center py-16"
        >
          <div class="w-24 h-24 bg-apple-light-gray rounded-full flex items-center justify-center mx-auto mb-6">
            <svg class="w-12 h-12 text-apple-text-secondary" fill="currentColor" viewBox="0 0 24 24">
              <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/>
            </svg>
          </div>
          <h3 class="text-xl font-semibold text-apple-text mb-2">暂无项目</h3>
          <p class="text-apple-text-secondary">该分类下暂无项目，请选择其他分类查看</p>
        </div>
      </div>
    </section>

    <!-- 项目统计 -->
    <section class="section-padding bg-apple-light-gray">
      <div class="container-max">
        <div class="grid grid-cols-1 md:grid-cols-4 gap-8 text-center">
          <div 
            v-for="stat in stats" 
            :key="stat.label"
            class="bg-white rounded-2xl p-8 shadow-lg"
          >
            <div class="text-3xl font-bold text-apple-blue mb-2">{{ stat.value }}</div>
            <div class="text-apple-text-secondary">{{ stat.label }}</div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref, computed } from 'vue'

const selectedCategory = ref('全部')

const categories = ['全部', 'Vue.js', 'React', '移动端', '全栈项目']

const projects = [
  {
    id: 1,
    name: '电商平台重构',
    description: '使用Vue 3和TypeScript重构大型电商平台，采用微前端架构，提升系统性能和用户体验。实现了商品管理、订单处理、用户管理等核心功能。',
    category: 'Vue.js',
    status: '已完成',
    technologies: ['Vue 3', 'TypeScript', 'Vite', 'Tailwind CSS', 'Pinia'],
    demoUrl: 'https://demo.example.com',
    githubUrl: 'https://github.com/example/ecommerce'
  },
  {
    id: 2,
    name: '数据可视化仪表板',
    description: '基于React和D3.js构建的实时数据可视化系统，支持多种图表类型，提供丰富的数据分析功能。',
    category: 'React',
    status: '已完成',
    technologies: ['React', 'D3.js', 'TypeScript', 'Ant Design', 'Redux'],
    demoUrl: 'https://demo.example.com',
    githubUrl: 'https://github.com/example/dashboard'
  },
  {
    id: 3,
    name: '移动端H5应用',
    description: '使用Vue 3开发的移动端H5应用，采用响应式设计，支持PWA功能，提供原生应用般的用户体验。',
    category: '移动端',
    status: '已完成',
    technologies: ['Vue 3', 'Vant', 'PWA', 'Vite', 'TypeScript'],
    demoUrl: 'https://demo.example.com',
    githubUrl: 'https://github.com/example/mobile-app'
  },
  {
    id: 4,
    name: '全栈博客系统',
    description: '基于Vue 3 + Node.js的全栈博客系统，包含文章管理、用户系统、评论功能等，采用JWT认证。',
    category: '全栈项目',
    status: '已完成',
    technologies: ['Vue 3', 'Node.js', 'Express', 'MongoDB', 'JWT'],
    demoUrl: 'https://demo.example.com',
    githubUrl: 'https://github.com/example/blog'
  },
  {
    id: 5,
    name: '企业管理系统',
    description: '使用React开发的企业级管理系统，包含用户管理、权限控制、数据统计等功能模块。',
    category: 'React',
    status: '开发中',
    technologies: ['React', 'TypeScript', 'Ant Design', 'Redux Toolkit', 'Axios'],
    demoUrl: null,
    githubUrl: 'https://github.com/example/admin'
  },
  {
    id: 6,
    name: '在线教育平台',
    description: '基于Vue 3的在线教育平台，支持视频播放、课程管理、学习进度跟踪等功能。',
    category: 'Vue.js',
    status: '已完成',
    technologies: ['Vue 3', 'Video.js', 'Element Plus', 'Vuex', 'Axios'],
    demoUrl: 'https://demo.example.com',
    githubUrl: 'https://github.com/example/education'
  }
]

const filteredProjects = computed(() => {
  if (selectedCategory.value === '全部') {
    return projects
  }
  return projects.filter(project => project.category === selectedCategory.value)
})

const stats = [
  { value: '15+', label: '完成项目' },
  { value: '5+', label: '技术栈' },
  { value: '3+', label: '年经验' },
  { value: '100%', label: '客户满意度' }
]
</script>

<style scoped>
.line-clamp-3 {
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
</style>
