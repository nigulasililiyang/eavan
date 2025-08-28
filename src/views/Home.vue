<template>
  <div class="home">
    <!-- 英雄区域 -->
    <section class="hero-section relative overflow-hidden">
      <div class="absolute inset-0 bg-gradient-to-br from-apple-blue/10 to-purple-600/10"></div>
      <div class="container-max section-padding relative z-10">
        <div class="text-center max-w-4xl mx-auto">
          <h1 class="text-hero font-bold text-apple-text mb-6 animate-fade-in">
            你好，我是
            <span class="text-gradient">杨雯</span>
          </h1>
          <p class="text-xl text-apple-text-secondary mb-8 animate-slide-up">
            一名充满激情的前端工程师，专注于创造优雅、高效的用户体验
          </p>
          <div class="flex flex-col sm:flex-row gap-4 justify-center animate-slide-up">
            <router-link to="/projects" class="btn-primary">
              查看作品
            </router-link>
            <router-link to="/contact" class="btn-secondary">
              联系我
            </router-link>
          </div>
        </div>
      </div>
      
      <!-- 装饰性背景元素 -->
      <div class="absolute top-1/4 left-1/4 w-32 h-32 bg-apple-blue/20 rounded-full blur-3xl"></div>
      <div class="absolute bottom-1/4 right-1/4 w-40 h-40 bg-purple-600/20 rounded-full blur-3xl"></div>
    </section>

    <!-- 技能展示区域 -->
    <section class="section-padding bg-apple-light-gray">
      <div class="container-max">
        <div class="text-center mb-16">
          <h2 class="text-large font-bold text-apple-text mb-4">专业技能</h2>
          <p class="text-apple-text-secondary max-w-2xl mx-auto">
            掌握现代前端技术栈，致力于构建高性能、可维护的Web应用
          </p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-8">
          <div 
            v-for="skill in skills" 
            :key="skill.name"
            class="bg-white rounded-2xl p-8 shadow-lg card-hover"
          >
            <div class="w-16 h-16 bg-apple-blue/10 rounded-2xl flex items-center justify-center mb-6">
              <component :is="skill.icon" class="w-8 h-8 text-apple-blue" />
            </div>
            <h3 class="text-xl font-semibold text-apple-text mb-3">{{ skill.name }}</h3>
            <p class="text-apple-text-secondary">{{ skill.description }}</p>
          </div>
        </div>
      </div>
    </section>

    <!-- 最新作品预览 -->
    <section class="section-padding">
      <div class="container-max">
        <div class="text-center mb-16">
          <h2 class="text-large font-bold text-apple-text mb-4">最新作品</h2>
          <p class="text-apple-text-secondary max-w-2xl mx-auto">
            探索我最近完成的项目，体验现代Web技术的魅力
          </p>
        </div>
        
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-12">
          <div 
            v-for="project in featuredProjects" 
            :key="project.id"
            class="group cursor-pointer"
            @click="goToProject(project.id)"
          >
            <div class="relative overflow-hidden rounded-2xl bg-apple-light-gray mb-6">
              <div class="aspect-video bg-gradient-to-br from-apple-blue/20 to-purple-600/20 flex items-center justify-center">
                <component :is="project.icon" class="w-16 h-16 text-apple-blue group-hover:scale-110 transition-transform duration-300" />
              </div>
            </div>
            <h3 class="text-xl font-semibold text-apple-text mb-2 group-hover:text-apple-blue transition-colors">
              {{ project.name }}
            </h3>
            <p class="text-apple-text-secondary mb-4">{{ project.description }}</p>
            <div class="flex flex-wrap gap-2">
              <span 
                v-for="tech in project.technologies" 
                :key="tech"
                class="px-3 py-1 bg-apple-light-gray text-apple-text-secondary text-sm rounded-full"
              >
                {{ tech }}
              </span>
            </div>
          </div>
        </div>
        
        <div class="text-center mt-12">
          <router-link to="/projects" class="btn-primary">
            查看所有作品
          </router-link>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { useRouter } from 'vue-router'

const router = useRouter()

const skills = [
  {
    name: '前端框架',
    description: '精通Vue.js、React等现代前端框架，能够构建复杂的企业级应用',
    icon: 'div'
  },
  {
    name: 'UI/UX设计',
    description: '注重用户体验设计，能够创建直观、美观的用户界面',
    icon: 'div'
  },
  {
    name: '性能优化',
    description: '深入理解Web性能优化，确保应用快速响应和流畅体验',
    icon: 'div'
  },
  {
    name: '响应式设计',
    description: '掌握移动优先的设计理念，适配各种设备和屏幕尺寸',
    icon: 'div'
  },
  {
    name: '现代工具链',
    description: '熟练使用Vite、Webpack等构建工具，提升开发效率',
    icon: 'div'
  },
  {
    name: '团队协作',
    description: '具备良好的沟通能力和团队协作精神，能够高效完成项目',
    icon: 'div'
  }
]

const featuredProjects = [
  {
    id: 1,
    name: '电商平台重构',
    description: '使用Vue 3和TypeScript重构大型电商平台，提升性能和用户体验',
    technologies: ['Vue 3', 'TypeScript', 'Vite', 'Tailwind CSS'],
    icon: 'div'
  },
  {
    id: 2,
    name: '数据可视化仪表板',
    description: '基于React和D3.js构建的实时数据可视化系统',
    technologies: ['React', 'D3.js', 'TypeScript', 'Ant Design'],
    icon: 'div'
  }
]

const goToProject = (projectId) => {
  router.push(`/projects#project-${projectId}`)
}
</script>

<style scoped>
.hero-section {
  min-height: 100vh;
  display: flex;
  align-items: center;
}
</style>
