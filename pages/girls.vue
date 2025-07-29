<template>
  <div class="min-h-screen bg-gradient-to-br from-gray-100 to-gray-200 text-gray-900 font-inter p-0 flex items-center justify-center">
    <div
      class="w-full sm:max-w-3xl bg-white rounded-xl shadow-xl border border-gray-300"
      :class="{
        'rounded-none shadow-none border-0': isMobile,
        'p-6 sm:p-10': !isMobile
      }"
    >
      <header class="mb-8 text-center px-4 sm:px-0">
        <h1 class="text-4xl sm:text-5xl font-extrabold mb-4 leading-tight">
          {{ pageContent.header.title }}
        </h1>
        <p class="text-lg text-gray-600">
          {{ pageContent.header.description }}
        </p>
      </header>

      <section class="space-y-8 px-0 ">
        <div
          v-for="(section, index) in pageContent.sections"
          :key="index"
          class="bg-gray-50 rounded-lg shadow-md border border-gray-200"
          :class="{
            'p-4': isMobile,
            'p-6': !isMobile
          }"
        >
          <h2 class="text-2xl sm:text-3xl font-bold mb-4 flex items-center text-gray-900">
            <svg
              class="w-8 h-8 mr-3"
              :class="section.icon.color"
              fill="currentColor"
              viewBox="0 0 24 24"
            >
              <path :d="section.icon.path" />
            </svg>
            {{ section.title }}
          </h2>
          <ul class="list-disc list-inside text-gray-700 mt-4 space-y-2">
            <li v-for="(item, itemIndex) in section.items" :key="itemIndex">
              <strong class="text-gray-900">{{ item.title }}</strong>
              <p class="ml-4 text-sm text-gray-600">{{ item.description }}</p>
            </li>
          </ul>
        </div>
      </section>

      <footer class="mt-10 text-center text-gray-500 text-sm px-4 sm:px-0">
        <p>{{ pageContent.footer.copyright }}</p>
        <p class="mt-2 text-red-500">
          {{ pageContent.footer.disclaimer }}
        </p>
      </footer>
    </div>
  </div>
</template>

<script setup>
import { ref, onMounted, onUnmounted } from 'vue'
import { useC } from '@/stores/girls.ts'

const pageContent = useC().pageC

const isMobile = ref(false)

function checkMobile() {
  isMobile.value = window.innerWidth < 640 // breakpoint sm: 640px
}

onMounted(() => {
  checkMobile()
  window.addEventListener('resize', checkMobile)
})

onUnmounted(() => {
  window.removeEventListener('resize', checkMobile)
})
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;700;800&display=swap');

body,html {
  font-family: 'Inter', sans-serif;
  margin: 0;

}
</style>
