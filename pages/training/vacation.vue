<template>
  <div class="min-h-screen bg-white text-gray-900 px-4 py-8 flex flex-col items-center">
    <h1 class="text-3xl font-bold mb-6">План на 20 дней отпуска</h1>

    <div class="grid gap-6 w-full max-w-3xl">
      <div
        v-for="(day, index) in days"
        :key="index"
        :class="['border-l-4 p-4 rounded shadow', day.color]"
      >
        <h2 class="text-2xl font-bold mb-2">{{ day.title }}</h2>
        <p v-if="day.description" class="italic text-gray-700 mb-2">{{ day.description }}</p>
        <ul v-if="day.exercises" class="list-disc pl-5 space-y-1">
          <li v-for="(exercise, i) in day.exercises" :key="i">{{ exercise }}</li>
        </ul>
      </div>
    </div>

    <p class="mt-6 text-gray-600">Далее повторяй цикл каждые 5 дней в течение всего отпуска.</p>
  </div>
</template>

<script setup>
const days = [
  {
    title: 'День 1 — Силовая тренировка A',
    description: 'Базовая силовая тренировка с акцентом на ноги и верх тела',
    exercises: [
      'Присед: 3×8×70 кг',
      'Жим лёжа: 3×8×70 кг',
      'Тяга в наклоне: 3×8–10×60 кг',
      'Сгибания рук с гантелями: 3×10×15 кг',
      'Face Pull: 3×12–15',
    ],
    color: 'bg-green-100 border-green-500',
  },
  {
    title: 'День 2 — Велопоездка',
    description: '60–90 минут, средний темп. В конце растяжка.',
    color: 'bg-blue-100 border-blue-500',
  },
  {
    title: 'День 3 — Силовая тренировка B',
    description: 'Фокус на спину, заднюю дельту и укрепление корпуса',
    exercises: [
      'Румынская тяга: 3×8×75 кг',
      'Жим гантелей на наклонной: 3×8×24 кг',
      'Тяга верхнего блока: 3×8×60 кг',
      'Подъём гантелей над головой сидя: 3×8×15 кг',
      'Разведения в наклоне: 3×12–15 (4–8 кг)',
    ],
    color: 'bg-green-100 border-green-500',
  },
  {
    title: 'День 4 — Отдых / пешая прогулка',
    description: 'Прогулка 40–60 минут, лёгкая растяжка всего тела.',
    color: 'bg-yellow-100 border-yellow-500',
  },
  {
    title: 'День 5 — Лёгкая круговая тренировка',
    exercises: [
      'Отжимания: 3×12–15',
      'Подтягивания или тяга резинки: 3×макс.',
      'Скручивания: 3×15',
      'Планка: 2×30 сек',
      'Подъёмы на носки: 4×20',
    ],
    color: 'bg-gray-100 border-gray-500',
  },
]

useSeoMeta({
  title: 'План на 20 дней отпуска',
  description: 'Подробный фитнес-план с силовыми, велопоездками и отдыхом',
  ogTitle: 'План на 20 дней отпуска',
  ogDescription: 'Максимально активный и структурированный план тренировок',
  ogImage: '/vacation.jpeg',
  twitterCard: 'summary_large_image',
})
</script>

<style scoped>
/* Дополнительные стили при необходимости */
</style>
