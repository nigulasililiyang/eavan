<template>
  <div class="about">
    <!-- 个人介绍区域 -->
    <section class="section-padding">
      <div class="container-max">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-16 items-center">
          <div class="space-y-8">
            <div>
              <h1 class="text-large font-bold text-apple-text mb-6">关于我</h1>
              <p class="text-lg text-apple-text-secondary leading-relaxed mb-6">
                我是一名充满激情的前端工程师，拥有5年的Web开发经验。我热爱创造优秀的用户体验，
                专注于构建高性能、可维护的现代Web应用。
              </p>
              <p class="text-lg text-apple-text-secondary leading-relaxed mb-6">
                我相信技术的力量能够改变世界，每一个像素、每一次交互都应该为用户带来价值。
                我不断学习新技术，保持对前沿技术的敏感度，致力于为用户创造更好的数字体验。
              </p>
            </div>
            
            <div class="flex flex-wrap gap-4">
              <div class="flex items-center space-x-2">
                <div class="w-3 h-3 bg-apple-blue rounded-full"></div>
                <span class="text-apple-text font-medium">5年+ 开发经验</span>
              </div>
              <div class="flex items-center space-x-2">
                <div class="w-3 h-3 bg-apple-blue rounded-full"></div>
                <span class="text-apple-text font-medium">50+ 项目经验</span>
              </div>
              <div class="flex items-center space-x-2">
                <div class="w-3 h-3 bg-apple-blue rounded-full"></div>
                <span class="text-apple-text font-medium">持续学习</span>
              </div>
            </div>
          </div>
          
          <div class="relative">
            <div class="bg-gradient-to-br from-apple-blue/20 to-purple-600/20 rounded-3xl p-8">
              <div class="aspect-square bg-white rounded-2xl flex items-center justify-center">
                <div class="text-center">
                  <div class="w-32 h-32 bg-apple-blue/10 rounded-full flex items-center justify-center mx-auto mb-6">
                    <svg class="w-16 h-16 text-apple-blue" fill="currentColor" viewBox="0 0 24 24">
                      <path d="M12 2C6.48 2 2 6.48 2 12s4.48 10 10 10 10-4.48 10-10S17.52 2 12 2zm-2 15l-5-5 1.41-1.41L10 14.17l7.59-7.59L19 8l-9 9z"/>
                    </svg>
                  </div>
                  <h3 class="text-xl font-semibold text-apple-text mb-2">杨雯</h3>
                  <p class="text-apple-text-secondary">前端工程师</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 技术栈区域 -->
    <section class="section-padding bg-apple-light-gray">
      <div class="container-max">
        <div class="text-center mb-16">
          <h2 class="text-large font-bold text-apple-text mb-4">技术栈</h2>
          <p class="text-apple-text-secondary max-w-2xl mx-auto">
            掌握现代前端技术栈，能够应对各种复杂的业务场景
          </p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-8">
          <div 
            v-for="category in techStack" 
            :key="category.name"
            class="bg-white rounded-2xl p-6 shadow-lg"
          >
            <h3 class="text-lg font-semibold text-apple-text mb-4">{{ category.name }}</h3>
            <div class="space-y-3">
              <div 
                v-for="tech in category.technologies" 
                :key="tech.name"
                class="flex items-center justify-between"
              >
                <span class="text-apple-text-secondary">{{ tech.name }}</span>
                <div class="w-20 bg-apple-light-gray rounded-full h-2">
                  <div 
                    class="bg-apple-blue h-2 rounded-full transition-all duration-500"
                    :style="{ width: tech.level + '%' }"
                  ></div>
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 工作经历 -->
    <section class="section-padding">
      <div class="container-max">
        <div class="text-center mb-16">
          <h2 class="text-large font-bold text-apple-text mb-4">工作经历</h2>
          <p class="text-apple-text-secondary max-w-2xl mx-auto">
            在不同公司和项目中积累的宝贵经验
          </p>
        </div>
        
        <div class="space-y-8">
          <div 
            v-for="experience in experiences" 
            :key="experience.id"
            class="bg-white rounded-2xl p-8 shadow-lg border border-gray-100"
          >
            <div class="flex flex-col lg:flex-row lg:items-center lg:justify-between mb-4">
              <div>
                <h3 class="text-xl font-semibold text-apple-text mb-2">{{ experience.title }}</h3>
                <p class="text-apple-blue font-medium">{{ experience.company }}</p>
              </div>
              <div class="text-apple-text-secondary mt-2 lg:mt-0">
                {{ experience.period }}
              </div>
            </div>
            <p class="text-apple-text-secondary mb-4">{{ experience.description }}</p>
            <div class="flex flex-wrap gap-2">
              <span 
                v-for="tech in experience.technologies" 
                :key="tech"
                class="px-3 py-1 bg-apple-light-gray text-apple-text-secondary text-sm rounded-full"
              >
                {{ tech }}
              </span>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 教育背景 -->
    <section class="section-padding bg-apple-light-gray">
      <div class="container-max">
        <div class="text-center mb-16">
          <h2 class="text-large font-bold text-apple-text mb-4">教育背景</h2>
          <p class="text-apple-text-secondary max-w-2xl mx-auto">
            扎实的学术基础为我的技术发展提供了强有力的支撑
          </p>
        </div>
        
        <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
          <div 
            v-for="education in educationList" 
            :key="education.id"
            class="bg-white rounded-2xl p-8 shadow-lg"
          >
            <div class="flex items-start space-x-4">
              <div class="w-12 h-12 bg-apple-blue/10 rounded-xl flex items-center justify-center flex-shrink-0">
                <svg class="w-6 h-6 text-apple-blue" fill="currentColor" viewBox="0 0 24 24">
                  <path d="M12 3L1 9l4 2.18v6L12 21l7-3.82v-6l2-1.09V17h2V9L12 3zm6.82 6L12 12.72 5.18 9 12 5.28 18.82 9zM17 15.99l-5 2.73-5-2.73v-3.72L12 15l5-2.73v3.72z"/>
                </svg>
              </div>
              <div class="flex-1">
                <h3 class="text-lg font-semibold text-apple-text mb-2">{{ education.degree }}</h3>
                <p class="text-apple-blue font-medium mb-2">{{ education.school }}</p>
                <p class="text-apple-text-secondary mb-2">{{ education.period }}</p>
                <p class="text-apple-text-secondary">{{ education.description }}</p>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
const techStack = [
  {
    name: '前端框架',
    technologies: [
      { name: 'Vue.js', level: 95 },
      { name: 'React', level: 90 },
      { name: 'Angular', level: 75 }
    ]
  },
  {
    name: '开发工具',
    technologies: [
      { name: 'TypeScript', level: 90 },
      { name: 'Vite/Webpack', level: 85 },
      { name: 'Git', level: 95 }
    ]
  },
  {
    name: 'UI/UX',
    technologies: [
      { name: 'Tailwind CSS', level: 95 },
      { name: 'Ant Design', level: 90 },
      { name: 'Figma', level: 80 }
    ]
  },
  {
    name: '后端技术',
    technologies: [
      { name: 'Node.js', level: 80 },
      { name: 'Express', level: 75 },
      { name: 'MongoDB', level: 70 }
    ]
  }
]

const experiences = [
  {
    id: 1,
    title: '高级前端工程师',
    company: '某知名互联网公司',
    period: '2022 - 至今',
    description: '负责公司核心产品的前端开发，带领团队完成多个重要项目的重构和优化，提升用户体验和系统性能。',
    technologies: ['Vue 3', 'TypeScript', 'Vite', 'Tailwind CSS', 'Node.js']
  },
  {
    id: 2,
    title: '前端工程师',
    company: '某科技公司',
    period: '2020 - 2022',
    description: '参与电商平台的前端开发，负责用户端和管理端的界面开发，优化页面性能和用户体验。',
    technologies: ['React', 'TypeScript', 'Ant Design', 'Redux', 'Webpack']
  },
  {
    id: 3,
    title: '初级前端工程师',
    company: '某创业公司',
    period: '2019 - 2020',
    description: '参与公司产品的从0到1开发，负责前端架构设计和核心功能实现。',
    technologies: ['Vue 2', 'JavaScript', 'Element UI', 'Axios']
  }
]

const educationList = [
  {
    id: 1,
    degree: '计算机科学与技术 学士学位',
    school: '某知名大学',
    period: '2015 - 2019',
    description: '主修计算机科学，专注于软件工程和Web开发技术，参与多个实践项目。'
  },
  {
    id: 2,
    degree: '前端开发认证',
    school: '某在线教育平台',
    period: '2019',
    description: '完成现代前端开发技术栈的深入学习，包括Vue.js、React等框架的实战应用。'
  }
]
</script>
