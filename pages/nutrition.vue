<template>
  <div class="bg-yellow-50 min-h-screen px-4 py-6 font-sans text-sm">
    <div class="max-w-5xl mx-auto">
      <h1 class="text-3xl font-extrabold text-yellow-800 mb-6 text-center uppercase tracking-wide">
        План питания (8-дневный цикл)
      </h1>

      <div v-for="(block, index) in dailyBlocks" :key="index" class="mb-8">
        <h2 class="text-xl font-bold text-white bg-yellow-700 px-4 py-2 rounded-t-md">
          {{ block.day }}
        </h2>

        <div class="bg-white shadow-md rounded-b-md overflow-hidden border border-yellow-300">
          <table class="w-full table-auto text-left">
            <thead class="bg-yellow-100 text-yellow-900 uppercase text-xs tracking-wider">
              <tr>
                <th class="px-4 py-2 border">Время</th>
                <th class="px-4 py-2 border">Приём пищи</th>
                <th class="px-4 py-2 border">Описание</th>
              </tr>
            </thead>
            <tbody>
              <tr
                v-for="(meal, mealIndex) in block.meals"
                :key="mealIndex"
                :class="{
                  'bg-yellow-200 font-semibold': isNextMeal(index, mealIndex),
                  'hover:bg-yellow-100': true
                }"
              >
                <td class="px-4 py-2 border align-top">{{ meal.time }}</td>
                <td class="px-4 py-2 border align-top text-yellow-800 font-semibold">
                  {{ meal.meal }}
                </td>
                <td class="px-4 py-2 border text-gray-800">{{ meal.description }}</td>
              </tr>
            </tbody>
          </table>
        </div>
      </div>
    </div>
  </div>
</template>

<script lang="ts" setup>
useSeoMeta({
  title: 'Питание | Мой План',
  description: 'Планируйте приёмы пищи, создавайте список покупок и отслеживайте рацион питания в соответствии с вашими целями.',
})

interface Meal {
  time: string
  meal: string
  description: string
}

interface DayBlock {
  day: string
  meals: Meal[]
}

// Сегодня — 7-й день
const todayIndex = 6

// Московское время
const now = new Date(new Date().toLocaleString('en-US', { timeZone: 'Europe/Moscow' }))
const currentMinutes = now.getHours() * 60 + now.getMinutes()

const dailyBlocks: DayBlock[] = [
  {
    day: 'День 1 — дневная смена',
    meals: [
      { time: '13:00', meal: 'Обед (в столовой)', description: 'Суп, каша, котлета или рыба, компот' },
      { time: '17:00', meal: 'Перекус', description: 'Творог или сыр с хлебцем, яблоко' },
      { time: '20:30', meal: 'Ужин', description: 'Нут/фасоль (150 г), тушёные овощи, яйцо или мясо (100–150 г), хлеб, молоко' }
    ]
  },
  {
    day: 'День 2 — дневная смена',
    meals: [
      { time: '13:00', meal: 'Обед (в столовой)', description: 'Суп, каша, котлета или рыба, компот' },
      { time: '17:00', meal: 'Перекус', description: 'Хлебец с сыром или яйцо, банан' },
      { time: '20:30', meal: 'Ужин', description: 'Картофель/рис + курица, овощи, масло, молоко' }
    ]
  },
  {
    day: 'День 3 — 1-я ночная',
    meals: [
      { time: '12:00', meal: 'Обед (дома)', description: 'Картофель, фасоль или нут, яйцо, салат, хлеб' },
      { time: '17:30', meal: 'Плотный приём пищи', description: 'Мясо (150 г), нут или фасоль (150 г), хлеб, овощи, молоко' },
      { time: '00:00', meal: 'Обед (в столовой)', description: 'Суп, каша, котлета, компот' },
      { time: '05:30', meal: 'Перекус', description: 'Йогурт, банан или молоко с хлебцем' }
    ]
  },
  {
    day: 'День 4 — 2-я ночная',
    meals: [
      { time: '08:30', meal: 'Завтрак (дома)', description: 'Яичница, тост, фасоль или нут, молоко' },
      { time: '09:00–16:00', meal: 'Сон', description: '' },
      { time: '18:30', meal: 'Ужин', description: 'Рис/макароны, рыба, салат, стакан молока' },
      { time: '00:00', meal: 'Обед (в столовой)', description: 'Суп, каша, котлета, компот' },
      { time: '05:00', meal: 'Перекус', description: 'Йогурт или молоко + банан' }
    ]
  },
  {
    day: 'День 5 — отсыпной',
    meals: [
      { time: '09:00', meal: 'Плотный завтрак', description: 'Омлет из 3 яиц, тост, фасоль, овощи, молоко' },
      { time: '14:00', meal: 'Обед', description: 'Рис + мясо/рыба + салат, хлеб, молоко' },
      { time: '18:00', meal: 'Лёгкий ужин', description: 'Нут + овощи, яйцо или сыр, хлеб' },
      { time: '22:30', meal: 'Перед сном', description: 'Картофельное пюре, тушёные овощи, мясо или омлет, молоко' }
    ]
  },
  {
    day: 'День 6 — тренировка',
    meals: [
      { time: '09:00', meal: 'Завтрак', description: 'Яичница, тост, фасоль, молоко' },
      { time: '12:00', meal: 'Тренировка', description: '' },
      { time: '13:30', meal: 'Обед', description: 'Рис, курица, овощи, хлеб, молоко' },
      { time: '18:00', meal: 'Ужин', description: 'Нут/чечевица, яйцо или сыр, овощи' },
      { time: '21:00', meal: 'Перекус', description: 'Творог или молоко, банан' }
    ]
  },
  {
    day: 'День 7 — отдых',
    meals: [
      { time: '10:00', meal: 'Завтрак', description: 'Картофель, яйца, салат, хлебец, молоко' },
      { time: '14:00', meal: 'Обед', description: 'Гречка/рис, курица, овощи' },
      { time: '18:00', meal: 'Ужин', description: 'Фасоль или чечевица, тушёные овощи, творог' },
      { time: '22:00', meal: 'Перекус', description: 'Молоко + печенье или орехи' }
    ]
  },
  {
    day: 'День 8 — тренировка',
    meals: [
      { time: '09:00', meal: 'Завтрак', description: 'Омлет, картофель, фасоль, салат, молоко' },
      { time: '12:00', meal: 'Тренировка', description: '' },
      { time: '13:30', meal: 'Обед', description: 'Макароны + рыба + овощи, хлеб, чай' },
      { time: '18:00', meal: 'Ужин', description: 'Чечевица или нут, яйца или сыр, овощи' },
      { time: '21:30', meal: 'Перекус', description: 'Йогурт или молоко + банан' }
    ]
  }
]

function timeToMinutes(time: string): number {
  const match = time.match(/^(\d{1,2}):(\d{2})/)
  if (!match) return Infinity
  return parseInt(match[1]) * 60 + parseInt(match[2])
}

function isNextMeal(dayIdx: number, mealIdx: number): boolean {
  if (dayIdx !== todayIndex) return false
  const meals = dailyBlocks[dayIdx].meals
  for (let i = 0; i < meals.length; i++) {
    if (timeToMinutes(meals[i].time) > currentMinutes) {
      return i === mealIdx
    }
  }
  return false
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css2?family=Barlow:wght@400;700;900&display=swap');

:root {
  font-family: 'Barlow', sans-serif;
}
</style>
