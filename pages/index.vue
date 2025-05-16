<template>
  <div class="min-h-screen bg-white text-gray-900 px-4 py-8 flex flex-col items-center">
    <div class="grid gap-8 w-full max-w-5xl">
      <NuxtLink
        v-for="item in sections"
        :key="item.to"
        :to="item.to"
        class="group relative overflow-hidden rounded-lg shadow-lg hover:shadow-2xl transition duration-300"
      >
        <img
          :src="item.image"
          :alt="item.title"
          class="w-full h-72 object-cover group-hover:scale-105 transition-transform duration-300"
        />
        <div class="absolute inset-0 flex items-center justify-center">
          <span class="text-4xl font-extrabold text-white drop-shadow-lg">{{ item.title }}</span>
        </div>
      </NuxtLink>
    </div>
  </div>
</template>

<script setup lang="ts">
useSeoMeta({
  title: 'Мой План — Тренировки, питание и показатели',
  description: 'Личный спортивный портал: тренировки, питание, сон и отслеживание прогресса в одном месте.',
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
    image: 'https://images.pexels.com/photos/1552249/pexels-photo-1552249.jpeg',
  },
  {
    to: '/nutrition',
    title: 'Питание',
    image: 'https://images.pexels.com/photos/1640777/pexels-photo-1640777.jpeg',
  },
  {
    to: '/metrics',
    title: 'Показатели',
    image: 'https://images.pexels.com/photos/267394/pexels-photo-267394.jpeg',
  },
  {
    to: '/sleep',
    title: 'Сон',
    image: 'https://images.pexels.com/photos/935743/pexels-photo-935743.jpeg', // Новая картинка
  },
]
</script>

<style scoped>
h2, h3 {
  font-family: 'Barlow', sans-serif;
}
</style>
