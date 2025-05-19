<template>
  <div class="max-w-xl mx-auto p-4 bg-white shadow-lg rounded-2xl">
    <h2 class="text-2xl font-bold mb-4 text-center">Чеклист здоровья</h2>

    <div v-for="(section, index) in checklist" :key="index" class="mb-6">
      <h3 class="text-xl font-semibold text-yellow-600 mb-2">{{ section.title }}</h3>
      <ul>
        <li
          v-for="(item, idx) in section.items"
          :key="idx"
          class="flex items-center gap-2 mb-1"
        >
          <input
            type="checkbox"
            :id="item.label"
            v-model="item.done"
            class="accent-yellow-500 w-5 h-5"
          />
          <label :for="item.label" class="text-gray-800">{{ item.label }}</label>
        </li>
      </ul>
    </div>

    <button
      class="mt-4 w-full bg-yellow-400 hover:bg-yellow-500 text-white font-bold py-2 px-4 rounded-xl"
      @click="saveChecklist"
    >
      Сохранить
    </button>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

interface ChecklistItem {
  label: string
  done: boolean
}

interface ChecklistSection {
  title: string
  items: ChecklistItem[]
}

const checklist = ref<ChecklistSection[]>([
  {
    title: 'Ежедневно',
    items: [
      { label: 'Сон 7+ часов', done: false },
      { label: '1.5–2 л воды', done: false },
      { label: '3–4 приёма пищи', done: false },
      { label: 'Овощи и фрукты (400 г)', done: false },
      { label: 'Витамин D (если нужно)', done: false },
      { label: '15+ мин дневного света', done: false },
      { label: 'Прогулка 30 мин', done: false },
      { label: 'Проветривание комнаты', done: false },
      { label: 'Стресс-контроль (дыхание, тишина)', done: false },
    ],
  },
  {
    title: 'В тренировочный день',
    items: [
      { label: 'Приём пищи до тренировки', done: false },
      { label: 'Тренировка по плану', done: false },
      { label: 'Вода во время тренировки', done: false },
      { label: 'Белковый приём пищи после', done: false },
      { label: 'Сон до 23:00', done: false },
    ],
  },
  {
    title: 'После ночной смены',
    items: [
      { label: 'Сон после смены (6–7 ч)', done: false },
      { label: 'Лёгкий приём пищи перед сном', done: false },
      { label: 'Вода после работы (500 мл)', done: false },
      { label: 'Свет и прогулка после пробуждения', done: false },
    ],
  },
])

// LocalStorage
const saveChecklist = () => {
  localStorage.setItem('healthChecklist', JSON.stringify(checklist.value))
}

onMounted(() => {
  const saved = localStorage.getItem('healthChecklist')
  if (saved) {
    checklist.value = JSON.parse(saved)
  }
})
</script>

<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}
</style>
