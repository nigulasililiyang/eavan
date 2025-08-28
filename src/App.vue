<template>
  <div id="app" class="min-h-screen">
    <!-- 导航栏 -->
    <nav class="fixed top-0 left-0 right-0 z-50 glass-effect">
      <div class="container-max px-6 py-4">
        <div class="flex items-center justify-between">
          <!-- Logo -->
          <router-link to="/" class="text-2xl font-bold text-apple-text hover:text-apple-blue transition-colors">
            Eavan Yang
          </router-link>
          
          <!-- 桌面端导航 -->
          <div class="hidden md:flex items-center space-x-8">
            <router-link 
              v-for="item in navItems" 
              :key="item.path"
              :to="item.path"
              class="text-apple-text hover:text-apple-blue transition-colors font-medium"
              :class="{ 'text-apple-blue': $route.path === item.path }"
            >
              {{ item.name }}
            </router-link>
          </div>
          
          <!-- 移动端菜单按钮 -->
          <button 
            @click="toggleMobileMenu"
            class="md:hidden p-2 rounded-lg hover:bg-gray-100 transition-colors"
          >
            <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
              <path v-if="!mobileMenuOpen" stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"></path>
              <path v-else stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"></path>
            </svg>
          </button>
        </div>
        
        <!-- 移动端菜单 -->
        <div 
          v-show="mobileMenuOpen"
          class="md:hidden mt-4 pb-4 border-t border-gray-200"
        >
          <div class="flex flex-col space-y-4 pt-4">
            <router-link 
              v-for="item in navItems" 
              :key="item.path"
              :to="item.path"
              @click="mobileMenuOpen = false"
              class="text-apple-text hover:text-apple-blue transition-colors font-medium"
              :class="{ 'text-apple-blue': $route.path === item.path }"
            >
              {{ item.name }}
            </router-link>
          </div>
        </div>
      </div>
    </nav>
    
    <!-- 主要内容区域 -->
    <main class="pt-20">
      <router-view v-slot="{ Component }">
        <transition name="page" mode="out-in">
          <component :is="Component" />
        </transition>
      </router-view>
    </main>
    
    <!-- 页脚 -->
    <footer class="bg-apple-light-gray mt-20">
      <div class="container-max section-padding">
        <div class="text-center">
          <p class="text-apple-text-secondary">
            © 2024 Eavan Yang. All rights reserved.
          </p>
        </div>
      </div>
    </footer>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const mobileMenuOpen = ref(false)

const navItems = [
  { name: '首页', path: '/' },
  { name: '关于我', path: '/about' },
  { name: '作品集', path: '/projects' },
  { name: '联系我', path: '/contact' }
]

const toggleMobileMenu = () => {
  mobileMenuOpen.value = !mobileMenuOpen.value
}
</script>

<style scoped>
.page-enter-active,
.page-leave-active {
  transition: all 0.3s ease;
}

.page-enter-from {
  opacity: 0;
  transform: translateY(20px);
}

.page-leave-to {
  opacity: 0;
  transform: translateY(-20px);
}
</style>
