<script setup lang="ts">
const steps = [
  'Сядь удобно (можно на стул или на пол, не обязательно лотос). Спина ровная, плечи расслаблены.',
  'Закрой или прикрой глаза. Смотри в одну точку перед собой, если глаза приоткрыты.',
  'Фокусируйся на дыхании. Наблюдай, как воздух входит и выходит, без усилий.',
  'Если приходят мысли — замечай их и мягко возвращай внимание к дыханию.',
  'Начни с 5–10 минут. Со временем можешь увеличить до 20 минут.'
]

const benefits = [
  'Снижает стресс, успокаивает.',
  'Улучшает концентрацию и внимание.',
  'Помогает лучше управлять эмоциями.',
  'Улучшает качество сна.',
  'Укрепляет ощущение контроля над собой.'
]

const recommendations = [
  'Утром — чтобы зарядиться и настроиться на день.',
  'Вечером — чтобы успокоиться и улучшить сон.',
  'В течение дня — когда нужно быстро перезагрузиться.'
]
</script>

<template>
  <div class="max-w-2xl mx-auto p-6">
    <h1 class="text-3xl font-bold mb-4">Медитация: пошаговое руководство</h1>

    <section class="mb-6">
      <h2 class="text-xl font-semibold mb-2">Как делать</h2>
      <ul class="list-disc list-inside space-y-1">
        <li v-for="(step, i) in steps" :key="i">{{ step }}</li>
      </ul>
    </section>

    <section class="mb-6">
      <h2 class="text-xl font-semibold mb-2">Польза</h2>
      <ul class="list-disc list-inside space-y-1">
        <li v-for="(benefit, i) in benefits" :key="i">{{ benefit }}</li>
      </ul>
    </section>

    <section>
      <h2 class="text-xl font-semibold mb-2">Когда лучше медитировать</h2>
      <ul class="list-disc list-inside space-y-1">
        <li v-for="(rec, i) in recommendations" :key="i">{{ rec }}</li>
      </ul>
    </section>
  </div>
</template>

<style scoped>
</style>
