<template>
  <div class="contact">
    <!-- 页面标题 -->
    <section class="section-padding bg-apple-light-gray">
      <div class="container-max text-center">
        <h1 class="text-large font-bold text-apple-text mb-6">联系我</h1>
        <p class="text-xl text-apple-text-secondary max-w-3xl mx-auto">
          如果您对我的作品感兴趣，或者有任何合作机会，欢迎随时联系我
        </p>
      </div>
    </section>

    <!-- 联系信息 -->
    <section class="section-padding">
      <div class="container-max">
        <div class="grid grid-cols-1 lg:grid-cols-2 gap-16">
          <!-- 联系表单 -->
          <div class="space-y-8">
            <div>
              <h2 class="text-2xl font-bold text-apple-text mb-4">发送消息</h2>
              <p class="text-apple-text-secondary mb-8">
                请填写下面的表单，我会尽快回复您的消息
              </p>
            </div>
            
            <form @submit.prevent="submitForm" class="space-y-6">
              <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                <div>
                  <label for="firstName" class="block text-sm font-medium text-apple-text mb-2">
                    姓名 *
                  </label>
                  <input
                    id="firstName"
                    v-model="form.firstName"
                    type="text"
                    required
                    class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-apple-blue focus:border-transparent transition-all duration-300"
                    placeholder="请输入您的姓名"
                  >
                </div>
                <div>
                  <label for="lastName" class="block text-sm font-medium text-apple-text mb-2">
                    姓氏
                  </label>
                  <input
                    id="lastName"
                    v-model="form.lastName"
                    type="text"
                    class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-apple-blue focus:border-transparent transition-all duration-300"
                    placeholder="请输入您的姓氏"
                  >
                </div>
              </div>
              
              <div>
                <label for="email" class="block text-sm font-medium text-apple-text mb-2">
                  邮箱地址 *
                </label>
                <input
                  id="email"
                  v-model="form.email"
                  type="email"
                  required
                  class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-apple-blue focus:border-transparent transition-all duration-300"
                  placeholder="请输入您的邮箱地址"
                >
              </div>
              
              <div>
                <label for="subject" class="block text-sm font-medium text-apple-text mb-2">
                  主题 *
                </label>
                <input
                  id="subject"
                  v-model="form.subject"
                  type="text"
                  required
                  class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-apple-blue focus:border-transparent transition-all duration-300"
                  placeholder="请输入消息主题"
                >
              </div>
              
              <div>
                <label for="message" class="block text-sm font-medium text-apple-text mb-2">
                  消息内容 *
                </label>
                <textarea
                  id="message"
                  v-model="form.message"
                  rows="6"
                  required
                  class="w-full px-4 py-3 border border-gray-300 rounded-lg focus:ring-2 focus:ring-apple-blue focus:border-transparent transition-all duration-300 resize-none"
                  placeholder="请详细描述您的需求或问题..."
                ></textarea>
              </div>
              
              <button
                type="submit"
                :disabled="isSubmitting"
                class="w-full btn-primary disabled:opacity-50 disabled:cursor-not-allowed"
              >
                <span v-if="isSubmitting">发送中...</span>
                <span v-else>发送消息</span>
              </button>
            </form>
          </div>
          
          <!-- 联系信息 -->
          <div class="space-y-8">
            <div>
              <h2 class="text-2xl font-bold text-apple-text mb-4">联系信息</h2>
              <p class="text-apple-text-secondary mb-8">
                您也可以通过以下方式直接联系我
              </p>
            </div>
            
            <div class="space-y-6">
              <div 
                v-for="contact in contactInfo" 
                :key="contact.type"
                class="flex items-start space-x-4 p-6 bg-white rounded-2xl shadow-lg"
              >
                <div class="w-12 h-12 bg-apple-blue/10 rounded-xl flex items-center justify-center flex-shrink-0">
                  <component :is="contact.icon" class="w-6 h-6 text-apple-blue" />
                </div>
                <div class="flex-1">
                  <h3 class="text-lg font-semibold text-apple-text mb-2">{{ contact.title }}</h3>
                  <p class="text-apple-text-secondary mb-2">{{ contact.value }}</p>
                  <a 
                    v-if="contact.link"
                    :href="contact.link"
                    class="text-apple-blue hover:text-apple-dark-blue transition-colors"
                  >
                    {{ contact.linkText }}
                  </a>
                </div>
              </div>
            </div>
            
            <!-- 社交媒体 -->
            <div class="bg-white rounded-2xl p-8 shadow-lg">
              <h3 class="text-xl font-semibold text-apple-text mb-6">关注我</h3>
              <div class="flex space-x-4">
                <a 
                  v-for="social in socialMedia" 
                  :key="social.name"
                  :href="social.url"
                  target="_blank"
                  class="w-12 h-12 bg-apple-light-gray rounded-xl flex items-center justify-center hover:bg-apple-blue hover:text-white transition-all duration-300"
                >
                  <component :is="social.icon" class="w-6 h-6" />
                </a>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>

    <!-- 工作时间 -->
    <section class="section-padding bg-apple-light-gray">
      <div class="container-max">
        <div class="text-center">
          <h2 class="text-large font-bold text-apple-text mb-6">工作时间</h2>
          <p class="text-apple-text-secondary mb-8 max-w-2xl mx-auto">
            我通常在以下时间段回复消息，如果您有紧急需求，请通过电话联系我
          </p>
          
          <div class="grid grid-cols-1 md:grid-cols-3 gap-8 max-w-4xl mx-auto">
            <div 
              v-for="schedule in workSchedule" 
              :key="schedule.day"
              class="bg-white rounded-2xl p-8 shadow-lg"
            >
              <h3 class="text-xl font-semibold text-apple-text mb-4">{{ schedule.day }}</h3>
              <p class="text-apple-text-secondary">{{ schedule.time }}</p>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const isSubmitting = ref(false)

const form = ref({
  firstName: '',
  lastName: '',
  email: '',
  subject: '',
  message: ''
})

const contactInfo = [
  {
    type: 'email',
    title: '邮箱地址',
    value: '136423275@qq.com',
    link: 'mailto:136423275@qq.com',
    linkText: '发送邮件',
    icon: 'div'
  },
  {
    type: 'phone',
    title: '联系电话',
    value: '+86 152-6881-3492',
    link: 'tel:+8615268813492',
    linkText: '拨打电话',
    icon: 'div'
  },
  {
    type: 'location',
    title: '工作地点',
    value: '杭州 / 远程工作',
    link: null,
    linkText: null,
    icon: 'div'
  }
]

const socialMedia = [
  {
    name: 'GitHub',
    url: 'https://github.com/nigulasililiyang',
    icon: 'div'
  },
  {
    name: 'LinkedIn',
    url: 'https://linkedin.com/in/eavan',
    icon: 'div'
  },
  {
    name: '微信',
    url: '#',
    icon: 'div'
  }
]

const workSchedule = [
  {
    day: '周一 - 周五',
    time: '9:00 AM - 6:00 PM'
  },
  {
    day: '周六',
    time: '10:00 AM - 4:00 PM'
  },
  {
    day: '周日',
    time: '休息日'
  }
]

const submitForm = async () => {
  isSubmitting.value = true
  
  // 模拟表单提交
  await new Promise(resolve => setTimeout(resolve, 2000))
  
  // 这里可以添加实际的表单提交逻辑
  console.log('表单数据:', form.value)
  
  // 重置表单
  form.value = {
    firstName: '',
    lastName: '',
    email: '',
    subject: '',
    message: ''
  }
  
  isSubmitting.value = false
  
  // 显示成功消息
  alert('消息发送成功！我会尽快回复您。')
}
</script>
