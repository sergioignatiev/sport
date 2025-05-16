<template>
  <div class="max-w-4xl mx-auto p-6">
    <h1 class="text-2xl font-bold text-yellow-800 mb-4">График сна (8-дневный цикл)</h1>

    <div v-for="(entry, i) in sleepSchedule" :key="i" class="mb-4 p-4 bg-yellow-50 rounded-md shadow border border-yellow-200">
      <h2 class="text-lg font-bold text-yellow-700 mb-2">{{ entry.day }}</h2>
      <ul class="text-sm text-gray-800 space-y-1">
        <li v-for="(slot, j) in entry.sleep" :key="j">🛌 {{ slot }}</li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts" setup>
useSeoMeta({
  title: 'Сон | Мой План',
  description: 'График сна с учётом сменной работы. Следите за восстановлением и качеством отдыха.',
})

interface DaySleep {
  day: string
  sleep: string[]
}

const sleepSchedule: DaySleep[] = [
  {
    day: 'День 1 — дневная смена',
    sleep: ['22:30 — 06:30']
  },
  {
    day: 'День 2 — дневная смена',
    sleep: ['22:30 — 06:30']
  },
  {
    day: 'День 3 — 1-я ночная',
    sleep: ['13:00 — 19:00']
  },
  {
    day: 'День 4 — 2-я ночная',
    sleep: ['09:00 — 16:00']
  },
  {
    day: 'День 5 — отсыпной',
    sleep: ['09:00 — 15:00']
  },
  {
    day: 'День 6 — тренировка',
    sleep: ['00:30 — 08:30']
  },
  {
    day: 'День 7 — отдых',
    sleep: ['00:30 — 08:30']
  },
  {
    day: 'День 8 — тренировка',
    sleep: ['00:30 — 08:30']
  }
]
</script>

<style scoped>
h1, h2 {
  font-family: 'Barlow', sans-serif;
}
</style>
