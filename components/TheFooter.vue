<template>
  <div class="flex flex-col ">
    

    <footer
      v-if="route.path !== '/'"
      class="bg-yellow-50 text-gray-700 text-sm text-center py-6 border-t border-yellow-200 shadow-inner"
    >
      <div class="max-w-5xl mx-auto px-4">
        <p class="mb-2 font-semibold">Связаться со мной:</p>
        <div class="flex justify-center space-x-6 text-yellow-700 font-medium">
          <span>Telegram</span>
          <span>Email</span>
          <span>LinkedIn</span>
        </div>
        <p class="mt-4 text-xs text-gray-500">© 2025 Мой План. Все права защищены.</p>
      </div>
    </footer>
  </div>
</template>

<script setup lang="ts">
import { useRoute } from 'vue-router'
const route = useRoute()
</script>
