<template>
  <div class="min-h-screen bg-white text-gray-900 px-4 py-8 flex flex-col items-center">
    <WorkoutCountdown/>

   

    <!-- Тренировки -->
    <div class="grid gap-6 w-full max-w-3xl">
      <div
        v-for="(session, index) in filteredSessions"
        :key="index"
        :class="[
          'border-l-4 p-4 rounded shadow',
          session.day === currentDay ? 'bg-yellow-200 border-yellow-600' : 'bg-yellow-100 border-yellow-500'
        ]"
      >
        <img
          v-if="session.image"
          :src="session.image"
          :alt="session.name"
          class="w-full h-48 object-cover rounded mb-4"
        />
        <h2 class="text-2xl font-bold mb-2">{{ session.name }}</h2>
        <p class="italic text-gray-700 mb-2">{{ session.description }}</p>
        <ul class="list-disc pl-5 space-y-1">
          <li v-for="(exercise, i) in session.exercises" :key="i">{{ exercise }}</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script setup>
useSeoMeta({
  title: 'Тренировки | Мой План',
  description: 'Ведите тренировочный дневник: добавляйте упражнения, отслеживайте прогресс, стройте программу тренировок.',
})

const currentDay = 1
const selectedDay = ref('all')

const trainingSessions = [
  {
    day: 1,
    name: 'Тренировка A (Full Body — 1-й выходной)',
    description: 'Базовая силовая тренировка',
    image: 'https://images.pexels.com/photos/2261477/pexels-photo-2261477.jpeg',
    exercises: [
      'Присед: 3×8×75 кг',
      'Жим лёжа: 3×8×70 кг',
      'Тяга в наклоне: 3×8–10 (50–55 кг)',
      'Сгибания рук на бицепс: 3×10–12',
      'Кор: планка и скручивания',
    ],
  },
  {
    day: 3,
    name: 'Тренировка B (2-й или 3-й выходной)',
    description: 'Силовой упор на спину, грудь и плечи',
    image: 'https://images.pexels.com/photos/4164767/pexels-photo-4164767.jpeg',
    exercises: [
      'Румынская тяга: 4×8×70 кг',
      'Жим гантелей под углом: 3×8–10',
      'Подтягивания: 3 подхода (по 4 повт.)',
      'Жим сидя гантелями: 3×10',
      'Подъёмы ног в висе',
    ],
  },
  {
    day: 0,
    name: 'Тренировка C (по желанию, лёгкая)',
    description: 'Лёгкая проработка вспомогательных мышц + кор',
    image: 'https://images.pexels.com/photos/1552242/pexels-photo-1552242.jpeg',
    exercises: [
      'Становая тяга с пустым грифом: 3×15',
      'Подъёмы на носки стоя: 4×20',
      'Французский жим: 3×10',
      'Тяга блока одной рукой: 3×12',
      'Ролик на пресс и растяжка',
    ],
  },
]

const filteredSessions = computed(() => {
  if (selectedDay.value === 'all') return trainingSessions
  return trainingSessions.filter((session) => session.day == selectedDay.value)
})
</script>
