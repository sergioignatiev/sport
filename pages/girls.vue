<template>
  <div class="min-h-screen bg-gradient-to-br from-gray-900 to-gray-800 text-gray-100 font-inter p-4 sm:p-8 flex items-center justify-center">
    <div class="max-w-4xl w-full bg-gray-700 rounded-xl shadow-2xl p-6 sm:p-10 border border-gray-600">
      <header class="mb-8 text-center">
        <h1 class="text-4xl sm:text-5xl font-extrabold text-white mb-4 leading-tight">
          {{ pageContent.header.title }}
        </h1>
        <p class="text-lg text-gray-300">
          {{ pageContent.header.description }}
        </p>
      </header>

      <section class="space-y-8">
        <div v-for="(section, index) in pageContent.sections" :key="index" class="bg-gray-800 p-6 rounded-lg shadow-lg border border-gray-600">
          <h2 class="text-2xl sm:text-3xl font-bold text-white mb-4 flex items-center">
            <svg class="w-8 h-8 mr-3" :class="section.icon.color" fill="currentColor" viewBox="0 0 24 24">
              <path :d="section.icon.path"/>
            </svg>
            {{ section.title }}
          </h2>
          <ul class="list-disc list-inside text-gray-300 mt-4 space-y-2">
            <li v-for="(item, itemIndex) in section.items" :key="itemIndex">
              <strong class="text-white">{{ item.title }}</strong>
              <p class="ml-4 text-sm text-gray-400">{{ item.description }}</p>
            </li>
          </ul>
        </div>
      </section>

      <footer class="mt-10 text-center text-gray-400 text-sm">
        <p>{{ pageContent.footer.copyright }}</p>
        <p class="mt-2 text-red-300">
          {{ pageContent.footer.disclaimer }}
        </p>
      </footer>
    </div>
  </div>
</template>

<script setup>
import {useC} from "@/stores/girls.ts"
const pageContent=useC().pageC

</script>

<style>
/* You can import Google Fonts here if needed, or rely on a global setup */
@import url('https://fonts.googleapis.com/css2?family=Inter:wght@400;700;800&display=swap');
body {
  font-family: 'Inter', sans-serif;
}
</style>
