<template>
  <div class="p-4 sm:p-6 bg-gray-50 min-h-screen font-sans flex justify-center">
    <div class="w-full max-w-2xl">
      <h1 class="text-2xl sm:text-3xl font-extrabold text-center text-gray-800 mb-6">Домашняя спина · 2x/нед</h1>

      <div v-for="(day, dayIndex) in spineRoutine" :key="dayIndex" class="bg-white rounded-xl shadow-lg p-5 mb-6">
        <h2 class="text-xl sm:text-2xl font-bold text-gray-900 mb-4">{{ day.name }}</h2>

        <div v-for="(block, blockIndex) in day.blocks" :key="blockIndex" class="mb-6 last:mb-0">
          <h3 class="text-lg sm:text-xl font-semibold text-gray-800 mb-3">{{ block.name }}</h3>
          <ul class="space-y-6">
            <li v-for="(exercise, exerciseIndex) in block.exercises" :key="exerciseIndex" class="pb-6 border-b last:border-b-0 border-gray-100">
              <h4 class="font-bold text-lg text-gray-800 mb-2">{{ exercise.name }}</h4>
              <p class="text-gray-600 text-base sm:text-lg font-semibold mb-3">{{ exercise.details }}</p>
              <div class="text-gray-700 text-base sm:text-base leading-relaxed space-y-2">
                <p class="font-medium">Как выполнять:</p>
                <ol class="list-decimal list-inside pl-2 space-y-1">
                  <li v-for="(step, sIndex) in exercise.howTo" :key="sIndex">{{ step }}</li>
                </ol>
              </div>
            </li>
          </ul>
        </div>
      </div>

      <div class="text-center text-gray-500 text-sm sm:text-base pt-4 leading-relaxed">
        Все упражнения без веса. Выполняйте медленно, с контролем.<br>
        Если какое-либо движение вызывает боль, исключите его.
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const spineRoutine = [
  {
    name: 'День 1: Фиксация + Мобилизация',
    blocks: [
      {
        name: 'Стабилизация кора',
        exercises: [
          {
            name: 'Bird-dog с паузой',
            details: '3 подхода по 8 повторений на каждую сторону, с паузой 2 секунды в верхней точке.',
            howTo: [
              'Встаньте на четвереньки: колени под бедрами, ладони под плечами, спина прямая.',
              'Одновременно вытяните правую руку вперед и левую ногу назад, удерживая их параллельно полу.',
              'Держите корпус стабильным, не допуская прогиба в пояснице.',
              'Задержитесь в этом положении на 2 секунды, затем медленно вернитесь в исходное положение.',
              'Повторите на другую сторону.'
            ]
          },
          {
            name: 'Glute bridge на одной ноге',
            details: '3 подхода по 8 повторений на каждую ногу.',
            howTo: [
              'Лягте на спину, согните колени, стопы стоят на полу на ширине плеч.',
              'Поднимите одну ногу вверх, выпрямляя ее в колене или согнув под 90 градусов.',
              'Опираясь на пятку стоящей ноги, поднимите таз максимально высоко, сжимая ягодицы.',
              'Удерживайте ровную линию от плеч до колена поднятой ноги.',
              'Медленно опуститесь вниз.'
            ]
          },
          {
            name: 'Wall dead-bug',
            details: '3 подхода по 10 повторений.',
            howTo: [
              'Лягте на спину, придвиньтесь ягодицами близко к стене.',
              'Поднимите ноги и руки вверх, упираясь стопами и ладонями в стену так, чтобы колени и локти были согнуты под углом 90 градусов, а поясница прижата к полу.',
              'Медленно опустите правую руку и левую ногу к полу, не отрывая поясницу.',
              'Вернитесь в исходное положение, затем повторите с другой стороны.'
            ]
          },
        ]
      },
      {
        name: 'Мобилизация позвоночника и таза',
        exercises: [
          {
            name: 'Кошка-корова + тазовые круги',
            details: 'По 1 минуте на каждое движение.',
            howTo: [
              '**Кошка-корова:** Встаньте на четвереньки. На вдохе прогните спину вниз, поднимая голову и копчик (поза коровы). На выдохе округлите спину, подтягивая подбородок к груди и подкручивая копчик (поза кошки). Плавно чередуйте эти движения.',
              '**Тазовые круги:** Из того же положения, начните делать круговые движения тазом в одну сторону, затем в другую, ощущая подвижность в пояснице и бедрах.'
            ]
          },
          {
            name: 'Дворники (windshield wipers)',
            details: '3 подхода по 10 повторений.',
            howTo: [
              'Лягте на спину, руки раскиньте в стороны (Т-образно), согните колени, стопы на полу, соедините колени и стопы вместе.',
              'Медленно опускайте оба колена вправо, стараясь при этом удерживать левое плечо на полу.',
              'Верните колени в центр, затем опустите их влево, стараясь удерживать правое плечо на полу.'
            ]
          },
        ]
      },
      {
        name: 'Изометрические удержания и дыхание',
        exercises: [
          {
            name: 'Планка на локтях',
            details: '3 подхода по 30–45 секунд удержания.',
            howTo: [
              'Лягте на живот, затем поднимитесь на локти и носки, предплечья параллельны друг другу.',
              'Удерживайте тело в прямой линии от головы до пяток, не прогибаясь в пояснице и не поднимая таз слишком высоко.',
              'Напрягите мышцы пресса и ягодицы.'
            ]
          },
          {
            name: 'Глубокое дыхание лёжа (вакуум)',
            details: '3 подхода.',
            howTo: [
              'Лягте на спину, согните колени, стопы на полу.',
              'Полностью выдохните весь воздух из легких, стараясь максимально опустошить живот.',
              'Задержите дыхание и максимально втяните живот под ребра, как будто пытаетесь прижать пупок к позвоночнику.',
              'Удерживайте это положение на несколько секунд, затем расслабьтесь и сделайте вдох.',
              'Повторите несколько раз.'
            ]
          },
        ]
      }
    ],
  },
  {
    name: 'День 2: Контроль + Устойчивость',
    blocks: [
      {
        name: 'Контроль и координация',
        exercises: [
          {
            name: 'Bird-dog с отведением руки',
            details: '3 подхода по 6 повторений.',
            howTo: [
              'Встаньте на четвереньки, как для обычного Bird-dog.',
              'Вытяните правую руку вперед и левую ногу назад.',
              'Затем, не опуская руку и ногу, медленно отведите вытянутую правую руку в сторону (примерно на 30-45 градусов), сохраняя стабильность корпуса.',
              'Верните руку вперед, затем опустите руку и ногу в исходное положение.',
              'Повторите с другой стороны.'
            ]
          },
          {
            name: 'Glute bridge с паузой',
            details: '3 подхода по 10 повторений.',
            howTo: [
              'Лягте на спину, согните колени, стопы на полу на ширине плеч.',
              'Поднимите таз максимально высоко, сжимая ягодицы.',
              'В верхней точке задержитесь на 2-3 секунды, сильно напрягая ягодицы.',
              'Медленно опуститесь вниз, контролируя движение.'
            ]
          },
          {
            name: 'Dead-bug с ногами на полу',
            details: '3 подхода по 10 повторений.',
            howTo: [
              'Лягте на спину, согните колени, стопы на полу. Поднимите руки вверх, перпендикулярно полу.',
              'Прижмите поясницу к полу (это ключевой момент!), напрягая пресс.',
              'Медленно опускайте правую руку назад за голову и скользите левой пяткой по полу, выпрямляя ногу.',
              'Следите, чтобы поясница не отрывалась от пола.',
              'Вернитесь в исходное положение и повторите с другой стороны.'
            ]
          },
          {
            name: 'Планка с отрывом руки',
            details: '3 подхода по 6 повторений (по 3 на каждую сторону).',
            howTo: [
              'Примите положение планки на прямых руках: ладони под плечами, тело образует прямую линию.',
              'Напрягите пресс и ягодицы, чтобы стабилизировать корпус.',
              'Медленно оторвите одну руку от пола и вытяните ее вперед или в сторону (как будто хотите что-то взять).',
              'Удерживайте тело ровным, избегая вращения таза.',
              'Верните руку на пол и повторите с другой стороны.'
            ]
          },
        ]
      },
      {
        name: 'Укрепление и осанка',
        exercises: [
          {
            name: 'Wall squat',
            details: '3 подхода по 20–30 секунд удержания.',
            howTo: [
              'Прислонитесь спиной к стене, ноги поставьте на ширине плеч, примерно в 30-60 см от стены.',
              'Медленно сползайте вниз по стене, пока колени не согнутся под углом 90 градусов, как будто вы сидите на невидимом стуле.',
              'Убедитесь, что поясница прижата к стене, а бедра параллельны полу.',
              'Удерживайте это положение, напрягая мышцы ног и кора.'
            ]
          },
          {
            name: 'Отрыв груди лёжа (без рук)',
            details: '3 подхода по 10 повторений.',
            howTo: [
              'Лягте на живот, руки положите вдоль тела ладонями вверх или сцепите за головой.',
              'Напрягите ягодицы и пресс, чтобы стабилизировать таз.',
              'Медленно поднимите верхнюю часть груди от пола, используя мышцы спины (как будто пытаетесь посмотреть вперед и вверх).',
              'Не запрокидывайте голову слишком сильно. Ноги остаются на полу.',
              'Медленно опуститесь вниз, контролируя движение.'
            ]
          },
        ]
      },
      {
        name: 'Мобилизация',
        exercises: [
          {
            name: 'Кошка-корова',
            details: '1 минута.',
            howTo: [
              'Встаньте на четвереньки, колени под бедрами, ладони под плечами.',
              'На вдохе: прогните спину, поднимая голову и копчик вверх (поза коровы).',
              'На выдохе: округлите спину, подтягивая подбородок к груди и подкручивая копчик (поза кошки).',
              'Плавно и ритмично чередуйте эти две позы, фокусируясь на движении позвоночника.'
            ]
          },
        ]
      }
    ],
  },
]
</script>

<style scoped>
/* Base styles for the body */
body {
  font-family: 'Inter', sans-serif; /* Consider linking Inter font from Google Fonts */
  background-color: #f0f2f5; /* Light background for a clean, modern look */
}

/* General spacing and padding for mobile-first */
.p-4 {
  padding: 1rem;
}
.sm\:p-6 {
  padding: 1.5rem; /* Applied on small screens and up */
}

/* Heading styles */
.text-2xl { font-size: 1.5rem; } /* Base for mobile */
.sm\:text-3xl { font-size: 1.875rem; } /* Larger on small screens and up */
.text-xl { font-size: 1.25rem; }
.sm\:text-2xl { font-size: 1.5rem; }
.text-lg { font-size: 1.125rem; }
.sm\:text-xl { font-size: 1.25rem; }
.text-base { font-size: 1rem; }
.sm\:text-base { font-size: 1rem; } /* Explicit for clarity, same as base */
.text-sm { font-size: 0.875rem; }
.sm\:text-sm { font-size: 0.875rem; } /* Explicit for clarity, same as base */
.text-xs { font-size: 0.75rem; }

/* Component specific styles */
.min-h-screen {
  min-height: 100vh;
}

.bg-gray-50 {
  background-color: #f9fafb;
}

.bg-white {
  background-color: #ffffff;
}

.rounded-xl {
  border-radius: 0.75rem;
}

.shadow-lg {
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
}

.text-gray-800 { color: #2d3748; }
.text-gray-900 { color: #1a202c; }
.text-gray-600 { color: #4a5568; }
.text-gray-700 { color: #4a5568; } /* Using the same gray for consistency */
.text-gray-500 { color: #a0aec0; }
.border-gray-100 { border-color: #f7fafc; }

/* Spacing utilities */
.mb-6 { margin-bottom: 1.5rem; }
.mb-4 { margin-bottom: 1rem; }
.mb-3 { margin-bottom: 0.75rem; }
.mb-2 { margin-bottom: 0.5rem; }
.pt-4 { padding-top: 1rem; }
.pb-6 { padding-bottom: 1.5rem; }
.space-y-6 > :not([hidden]) ~ :not([hidden]) { margin-top: 1.5rem; }
.space-y-4 > :not([hidden]) ~ :not([hidden]) { margin-top: 1rem; }
.space-y-2 > :not([hidden]) ~ :not([hidden]) { margin-top: 0.5rem; }
.space-y-1 > :not([hidden]) ~ :not([hidden]) { margin-top: 0.25rem; }
.pl-2 { padding-left: 0.5rem; }
.list-inside { list-style-position: inside; }

/* Font weights */
.font-extrabold { font-weight: 800; }
.font-bold { font-weight: 700; }
.font-semibold { font-weight: 600; }
.font-medium { font-weight: 500; }

/* Text alignment */
.text-center { text-align: center; }

/* Line height */
.leading-relaxed { line-height: 1.625; }

/* Border utility */
.border-b { border-bottom-width: 1px; }
.last\:border-b-0:last-child { border-bottom-width: 0px; } /* Removes border from the last item */

/* Flex utilities for centering content */
.flex { display: flex; }
.justify-center { justify-content: center; }

/* Width utilities */
.w-full { width: 100%; }
.max-w-2xl { max-width: 42rem; /* Tailwind's default max-width for 2xl */ }
</style>