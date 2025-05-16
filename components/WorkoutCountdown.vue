<template>
  <div class="text-center p-6">
    <p class="text-lg text-gray-700 font-semibold mb-2">До следующей тренировки осталось:</p>
    <p class="text-4xl font-bold text-yellow-600">{{ timeRemaining }}</p>
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from 'vue'

const timeRemaining = ref('')

const getNextWorkoutDate = (): Date => {
  const now = new Date()
  now.setSeconds(0, 0)

  const daysUntilWorkout = 6 // сегодня 2-й выходной, завтра отдых, затем 2д + 2н + отсыпной
  const workoutDate = new Date(now)
  workoutDate.setDate(workoutDate.getDate() + daysUntilWorkout)
  workoutDate.setHours(10, 0, 0, 0)
  return workoutDate
}

const updateCountdown = () => {
  const now = new Date()
  const workoutDate = getNextWorkoutDate()
  const diffMs = workoutDate.getTime() - now.getTime()

  if (diffMs <= 0) {
    timeRemaining.value = 'Сегодня в 10:00'
    return
  }

  const totalMinutes = Math.floor(diffMs / 60000)
  const days = Math.floor(totalMinutes / (60 * 24))
  const hours = Math.floor((totalMinutes % (60 * 24)) / 60)
  const minutes = totalMinutes % 60

  timeRemaining.value = `${days}д ${hours}ч ${minutes}м`
}

onMounted(() => {
  updateCountdown()
  setInterval(updateCountdown, 60000)
})
</script>
