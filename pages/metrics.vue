<template>
  <div class="max-w-5xl mx-auto bg-white p-6 rounded-lg shadow-md mt-6">
    <h2 class="text-2xl font-bold mb-4 text-blue-700">📅 Тренировочный дневник</h2>

    <!-- Календарь -->
    <div class="mb-4">
      <label for="currentDate" class="block text-sm font-semibold mb-1">Дата тренировки:</label>
      <input
        id="currentDate"
        type="date"
        v-model="selectedDate"
        class="border rounded px-3 py-2 w-full max-w-xs"
        :class="{'ring-2 ring-yellow-500': hasWorkout(selectedDate)}"
      />
    </div>

    <!-- Таблица упражнений -->
    <table class="w-full table-auto border border-gray-300 text-sm">
      <thead class="bg-gray-100">
        <tr>
          <th class="border px-2 py-2 text-left">Упражнение</th>
          <th class="border px-2 py-2">Подходы</th>
          <th class="border px-2 py-2">Повторы</th>
          <th class="border px-2 py-2">Вес (кг)</th>
          <th class="border px-2 py-2 text-center">Удалить</th>
        </tr>
      </thead>
      <tbody>
        <tr
          v-for="(exercise, index) in log[selectedDate] || []"
          :key="index"
          class="hover:bg-yellow-50 transition"
        >
          <td class="border px-2 py-1">
            <select v-model="exercise.name" class="w-full border rounded px-2 py-1">
              <option disabled value="">Выберите упражнение</option>
              <option v-for="option in recommendedExercises" :key="option">{{ option }}</option>
            </select>
          </td>
          <td class="border px-2 py-1">
            <input
              v-model.number="exercise.sets"
              type="number"
              min="1"
              class="w-full border rounded px-2 py-1 text-center"
            />
          </td>
          <td class="border px-2 py-1">
            <input
              v-model.number="exercise.reps"
              type="number"
              min="1"
              class="w-full border rounded px-2 py-1 text-center"
            />
          </td>
          <td class="border px-2 py-1">
            <input
              v-model.number="exercise.weight"
              type="number"
              min="0"
              class="w-full border rounded px-2 py-1 text-center"
            />
          </td>
          <td class="border px-2 py-1 text-center">
            <button
              @click="removeExercise(index)"
              class="text-red-500 hover:text-red-700 font-bold"
              title="Удалить"
            >
              ✖
            </button>
          </td>
        </tr>
      </tbody>
    </table>

    <!-- Кнопка добавить и счётчик -->
    <div class="mt-4 flex justify-between items-center">
      <button
        @click="addExercise"
        class="bg-yellow-400 hover:bg-yellow-500 text-black font-bold py-2 px-4 rounded"
      >
        ➕ Добавить
      </button>
      <p class="text-sm text-gray-500">Всего: {{ log[selectedDate]?.length || 0 }} упражнений</p>
    </div>

    <!-- История тренировок -->
    <div class="mt-10">
      <h3 class="text-lg font-semibold mb-2 text-gray-800">📈 История тренировок:</h3>
      <ul class="space-y-2 text-sm text-gray-600">
        <li v-for="date in sortedDates" :key="date">
          <strong>{{ date }}:</strong>
          {{ log[date].length }} упражнений
        </li>
      </ul>
    </div>
  </div>
</template>

<script lang="ts" setup>
import { ref, reactive, watch, computed, onMounted } from 'vue'

interface Exercise {
  name: string
  sets: number
  reps: number
  weight: number
}

type WorkoutLog = {
  [date: string]: Exercise[]
}

const today = new Date().toISOString().split('T')[0]
const selectedDate = ref<string>(today)

const defaultExercises: Exercise[] = [
  { name: 'Приседания', sets: 3, reps: 8, weight: 75 },
  { name: 'Жим лёжа', sets: 3, reps: 8, weight: 70 },
]

const recommendedExercises = [
  'Приседания',
  'Жим лёжа',
  'Румынская тяга',
  'Подтягивания',
  'Тяга верхнего блока',
  'Армейский жим',
  'Становая тяга',
  'Тяга гантели в наклоне',
]

const log = reactive<WorkoutLog>({})

onMounted(() => {
  const saved = localStorage.getItem('trainingLog')
  if (saved) {
    Object.assign(log, JSON.parse(saved))
  } else {
    log[today] = JSON.parse(JSON.stringify(defaultExercises))
  }
})

watch(
  log,
  () => {
    localStorage.setItem('trainingLog', JSON.stringify(log))
  },
  { deep: true }
)

function addExercise(): void {
  if (!log[selectedDate.value]) {
    log[selectedDate.value] = []
  }
  log[selectedDate.value].push({
    name: '',
    sets: 3,
    reps: 10,
    weight: 0,
  })
}

function removeExercise(index: number): void {
  log[selectedDate.value].splice(index, 1)
}

const sortedDates = computed(() =>
  Object.keys(log).sort((a, b) => new Date(b).getTime() - new Date(a).getTime())
)

function hasWorkout(date: string): boolean {
  return !!log[date] && log[date].length > 0
}
</script>

<style scoped>
input[type='date'].ring-2 {
  outline: none;
}
</style>
