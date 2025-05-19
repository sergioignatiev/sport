<template>
  <div class="max-w-2xl mx-auto p-4 space-y-6">
    <div class="flex justify-between items-center">
      <h1 class="text-2xl font-bold text-rose-700">Чеклист восстановления при боли в горле</h1>
      <button
        @click="toggleSick"
        class="text-sm bg-rose-500 text-white px-3 py-1 rounded-xl hover:bg-rose-600 transition"
      >
        {{ isSick ? 'Я здоров' : 'Я заболел' }}
      </button>
    </div>

    <div v-if="showChecklist" class="space-y-6">
      <section v-for="(section, idx) in checklist" :key="idx" class="bg-white rounded-2xl p-4 shadow">
        <h2 class="text-xl font-semibold mb-3 text-gray-800">{{ section.title }}</h2>
        <ul class="space-y-2">
          <li v-for="(item, index) in section.tasks" :key="index" class="flex items-start gap-2">
            <input type="checkbox" v-model="item.done" class="mt-1">
            <span :class="{ 'line-through text-gray-400': item.done }">{{ item.label }}</span>
          </li>
        </ul>
      </section>

      <div class="text-center">
        <button @click="resetChecklist" class="bg-rose-600 text-white px-4 py-2 rounded-xl hover:bg-rose-700 transition">
          Сбросить чеклист
        </button>
      </div>
    </div>

    <div v-else class="text-center text-gray-500 mt-10">
      Сегодня не день восстановления — чеклист не нужен
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref, reactive, computed } from 'vue'

interface Task {
  label: string
  done: boolean
}

interface Section {
  title: string
  tasks: Task[]
}

const cycleStartDate = '2025-05-10'

function getCycleDay(startDate: string): number {
  const msPerDay = 1000 * 60 * 60 * 24
  const now = new Date()
  const start = new Date(startDate)
  const daysPassed = Math.floor((+now - +start) / msPerDay)
  return (daysPassed % 8) + 1
}

const cycleDay = getCycleDay(cycleStartDate)
const isSick = ref(false)
const toggleSick = () => isSick.value = !isSick.value
const showChecklist = computed(() => isSick.value || cycleDay === 5 || cycleDay === 8)

const checklist = reactive<Section[]>([
  {
    title: '🌡 Утро',
    tasks: [
      { label: 'Выпить тёплую воду с лимоном или мёдом', done: false },
      { label: 'Оценить состояние: температура, налёт, слабость', done: false },
      { label: 'Полоскание: соль + сода (1 стакан)', done: false },
      { label: 'Проветрить комнату', done: false },
      { label: 'Увлажнить воздух в комнате', done: false },
    ]
  },
  {
    title: '☀️ Днём',
    tasks: [
      { label: 'Пить воду или чай каждые 1–1.5 часа', done: false },
      { label: 'Полоскание или спрей для горла', done: false },
      { label: 'Тёплая еда без острого и кислого', done: false },
      { label: 'Сосательные таблетки (до 6–8 в день)', done: false },
      { label: 'Голосовой покой (не шептать)', done: false },
    ]
  },
  {
    title: '🌙 Вечер',
    tasks: [
      { label: 'Полоскание перед сном', done: false },
      { label: 'Тёплый душ или ванночка для ног', done: false },
      { label: 'Пить тёплую воду или чай перед сном', done: false },
      { label: 'Проветрить и увлажнить спальню', done: false },
      { label: 'Сон не менее 7–8 часов', done: false },
    ]
  },
  {
    title: '🧄 Натуральные средства (по желанию)',
    tasks: [
      { label: 'Чеснок (½ зубчика в день)', done: false },
      { label: 'Мёд (1 ч.л. под язык или в воду)', done: false },
      { label: 'Имбирь (в чай или жевать)', done: false },
      { label: 'Лимон (в тёплую воду или чай)', done: false },
    ]
  }
])

const resetChecklist = () => {
  checklist.forEach(section => section.tasks.forEach(task => task.done = false))
}
</script>

<style scoped>
body {
  background-color: #fffaf9;
}
</style>
