<template>
  <nav v-if="showNavbar" ref="navbarRef" class="bg-yellow-700 text-white shadow sticky top-0 z-50">
    <div class="max-w-6xl mx-auto px-4">
      <div class="flex justify-between items-center h-14">
        <!-- Логотип -->
        <NuxtLink to="/" class="text-xl font-bold tracking-wide hover:text-yellow-200">
          🏋️ Мой План
        </NuxtLink>

        <!-- Десктоп меню -->
        <div class="hidden md:flex space-x-6 text-sm font-semibold">
          <NuxtLink to="/training" class="hover:text-yellow-300">Тренировки</NuxtLink>
          <NuxtLink to="/nutrition" class="hover:text-yellow-300">Питание</NuxtLink>
          <NuxtLink to="/metrics" class="hover:text-yellow-300">Показатели</NuxtLink>
             <NuxtLink to="/sleep" class="hover:text-yellow-300">Сон</NuxtLink>
        </div>

        <!-- Бургер -->
        <button @click="toggleMenu" class="md:hidden focus:outline-none" aria-label="Меню">
          <svg class="h-6 w-6" fill="none" stroke="currentColor" stroke-width="2"
               viewBox="0 0 24 24" stroke-linecap="round" stroke-linejoin="round">
            <path v-if="!isOpen" d="M4 6h16M4 12h16M4 18h16"/>
            <path v-else d="M6 18L18 6M6 6l12 12"/>
          </svg>
        </button>
      </div>
    </div>

    <!-- Мобильное меню -->
    <div v-if="isOpen" class="md:hidden bg-yellow-600 px-4 pb-3 space-y-2 text-sm font-semibold">
      <NuxtLink to="/training" class="block py-2 hover:text-yellow-300" @click="closeMenu">Тренировки</NuxtLink>
      <NuxtLink to="/nutrition" class="block py-2 hover:text-yellow-300" @click="closeMenu">Питание</NuxtLink>
      <NuxtLink to="/metrics" class="block py-2 hover:text-yellow-300" @click="closeMenu">Показатели</NuxtLink>
      <NuxtLink to="/sleep" class="block py-2 hover:text-yellow-300" @click="closeMenu">Сон</NuxtLink>
    </div>
  </nav>
</template>

<script lang="ts" setup>
import { ref, onMounted, onBeforeUnmount, computed } from 'vue'
import { useRoute } from 'vue-router'

const isOpen = ref(false)
const route = useRoute()
const navbarRef = ref<HTMLElement | null>(null)

const showNavbar = computed(() => route.path !== '/')

const toggleMenu = () => {
  isOpen.value = !isOpen.value
}

const closeMenu = () => {
  isOpen.value = false
}

function handleClickOutside(event: MouseEvent) {
  const target = event.target as Node
  if (isOpen.value && navbarRef.value && !navbarRef.value.contains(target)) {
    closeMenu()
  }
}

onMounted(() => {
  document.addEventListener('click', handleClickOutside)
})

onBeforeUnmount(() => {
  document.removeEventListener('click', handleClickOutside)
})
</script>

<style scoped>
nav {
  font-family: 'Barlow', sans-serif;
}
</style>
