<template>
  <div class="min-h-screen bg-white text-gray-900 px-4 py-8 flex flex-col items-center">
    <div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-8 w-full max-w-7xl">
      <NuxtLink
        v-for="item in sections"
        :key="item.to"
        :to="item.to"
        class="group relative overflow-hidden rounded-2xl shadow-lg hover:shadow-2xl transition duration-300"
      >
        <img
          :src="item.image"
          :alt="item.title"
          class="w-full h-72 object-cover group-hover:scale-105 transition-transform duration-300"
        />
        <div class="absolute inset-0 flex items-center justify-center bg-black/30">
          <span class="text-3xl sm:text-4xl font-extrabold text-white drop-shadow-xl text-center px-4">{{ item.title }}</span>
        </div>
      </NuxtLink>
    </div>
  </div>
</template>

<script setup lang="ts">
useSeoMeta({
  title: 'Мой План — Всё в одном: спорт, здоровье и язык',
  description: 'Тренировки, питание, сон, восстановление, здоровье и изучение испанского — всё на одной странице.',
})

interface Section {
  to: string
  title: string
  image: string
}

const sections: Section[] = [
  {
    to: '/training',
    title: 'Тренировки',
    image: 'training.jpeg',
  },
  {
    to: '/nutrition',
    title: 'Питание',
    image: 'nutrition.jpeg',
  },
  {
    to: '/metrics',
    title: 'Показатели',
    image: 'metrics.jpeg',
  },
  {
    to: '/sleep',
    title: 'Сон',
    image: 'sleep.jpeg',
  },
  {
    to: '/recovery',
    title: 'Восстановление',
    image: 'recovery.jpeg',
  },
  {
    to: '/checklist',
    title: 'Чеклист здоровья',
    image: 'checklist.jpeg',
  },
  {
    to: '/espanol',
    title: 'Español',
    image: 'espana.png',
  },
]
</script>

<style scoped>
h2, h3 {
  font-family: 'Barlow', sans-serif;
}
</style>
