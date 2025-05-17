<template>
  <div class="p-6 max-w-xl mx-auto">
    <h1 class="text-2xl font-bold mb-4">Персональные данные</h1>
    <form @submit.prevent="saveData" class="grid gap-4">
      <input v-model="form.goal" placeholder="Цель (масса, сушка...)" class="input" />
      <input v-model="form.weight" type="number" placeholder="Вес (кг)" class="input" />
      <input v-model="form.height" type="number" placeholder="Рост (см)" class="input" />
      <input v-model="form.trainingsPerWeek" type="number" placeholder="Тренировок в неделю" class="input" />
      <textarea v-model="form.schedule" placeholder="График смен (опционально)" class="input" />
      <button class="bg-blue-600 text-white px-4 py-2 rounded">Сохранить</button>
    </form>
    <NuxtLink to="/plan" class="mt-4 inline-block text-blue-600 underline">Перейти к плану</NuxtLink>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

const form = ref({
  goal: '',
  weight: '',
  height: '',
  trainingsPerWeek: '',
  schedule: ''
})

onMounted(() => {
  const saved = localStorage.getItem('userData')
  if (saved) form.value = JSON.parse(saved)
})

function saveData() {
  localStorage.setItem('userData', JSON.stringify(form.value))
  alert('Данные сохранены!')
}
</script>

<style scoped>
.input {
  @apply border p-2 rounded w-full;
}
</style>