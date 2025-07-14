<template>
  <div class="min-h-screen bg-white text-gray-900 px-4 py-8 flex flex-col items-center">
    <h1 class="text-3xl font-bold mb-6">Мои тренировки</h1>

    <!-- Сетка тренировок -->
    <div class="grid gap-6 w-full max-w-3xl">

      <!-- Тренировка A -->
      <div class="bg-yellow-100 border-l-4 border-yellow-500 p-4 rounded shadow">
        <img
          src="https://images.pexels.com/photos/2261477/pexels-photo-2261477.jpeg"
          alt="Тренировка A"
          class="w-full h-48 object-cover rounded mb-4"
        />
        <h2 class="text-2xl font-bold mb-2">Тренировка A (ноги, грудь, спина)</h2>
        <p class="italic text-gray-700 mb-2">Базовая силовая тренировка с акцентом на ноги и верх тела</p>
        <ul class="list-disc pl-5 space-y-1">
          <li>Приседания со штангой: 3×8 × 70 кг</li>
          <li>Жим штанги лёжа: 3×8 × 70 кг</li>
          <li>Тяга штанги в наклоне: 3×8–10 × 60 кг</li>
          <li>Гантели на бицепс стоя: 3×8–10 × 15 кг</li>
          <li>Face Pull (резинка к лицу): 3×12–15</li>
        </ul>
      </div>

      <!-- Тренировка B -->
      <div class="bg-yellow-100 border-l-4 border-yellow-500 p-4 rounded shadow">
        <img
          src="https://images.pexels.com/photos/4164767/pexels-photo-4164767.jpeg"
          alt="Тренировка B"
          class="w-full h-48 object-cover rounded mb-4"
        />
        <h2 class="text-2xl font-bold mb-2">Тренировка B (задняя цепь, плечи, осанка)</h2>
        <p class="italic text-gray-700 mb-2">Фокус на спину, заднюю дельту и укрепление корпуса</p>
        <ul class="list-disc pl-5 space-y-1">
          <li>Румынская тяга: 3×8 × 75 кг</li>
          <li>Жим гантелей на наклонной скамье: 3×8 × 24 кг</li>
          <li>Тяга верхнего блока к груди: 3×8 × 60 кг</li>
          <li>Подъём гантелей над головой сидя: 3×8 × 15 кг</li>
          <li>Разведения гантелей в наклоне: 3×12–15 (4–8 кг)</li>
        </ul>
      </div>

      <!-- В конце каждой тренировки -->
      <div class="bg-yellow-50 border-l-4 border-yellow-400 p-4 rounded shadow">
        <h2 class="text-xl font-bold mb-2">В конце каждой тренировки</h2>
        <p class="italic text-gray-700 mb-2">Закрепление осанки и укрепление корпуса</p>
        <ul class="list-disc pl-5 space-y-1">
          <li>Растяжка грудных у стены: 2–3 подхода по 30 секунд</li>
          <li>Планка (либо супермен): 2–3 подхода по 30 секунд</li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script setup>
useSeoMeta({
  title: 'Мой фитнес-план',
  description: 'Детальная программа тренировок с упором на массу, спину и осанку',
  ogTitle: 'Мой фитнес-план',
  ogDescription: 'Создавай, отслеживай и совершенствуй свою программу тренировок',
  ogImage: '/training.jpeg',
  twitterCard: 'summary_large_image',
})
</script>

<style scoped>
/* Дополнительные стили при необходимости */
</style>