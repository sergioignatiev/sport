<template>
  <div class="min-h-screen bg-gray-100 py-10 px-6">
    <div class="max-w-4xl mx-auto">
      <h1 class="text-4xl font-bold mb-8 text-gray-800">Recommended Books</h1>

      <div class="space-y-6">
        <div
          v-for="(book, index) in books"
          :key="index"
          class="bg-white p-6 rounded-2xl shadow-md"
        >
          <div class="flex justify-between items-start">
            <div>
              <h2 class="text-xl font-semibold text-gray-900">{{ book.title }}</h2>
              <p class="text-sm text-gray-500 mb-2">by {{ book.author }}</p>
              <p class="text-gray-700">{{ book.description }}</p>
            </div>
            <span class="ml-4 text-sm px-3 py-1 bg-blue-100 text-blue-700 rounded-full whitespace-nowrap">{{ book.tag }}</span>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
const books = [
  {
    title: 'Essentialism',
    author: 'Greg McKeown',
    description: 'Cut distractions. Focus only on what matters. You already have this — read it first.',
    tag: '🔖 Read First'
  },
  {
    title: 'Atomic Habits',
    author: 'James Clear',
    description: 'Tactical system to build and sustain habits that stick. No fluff.',
    tag: 'Step 2'
  },
  {
    title: 'Deep Work',
    author: 'Cal Newport',
    description: 'Learn to focus deeply in a world built to distract you. Essential for execution.',
    tag: 'Step 3'
  },
  {
    title: 'The Almanack of Naval Ravikant',
    author: 'Eric Jorgenson',
    description: 'Clear thinking on wealth, health, and leverage. Game-changing mindsets.',
    tag: 'Step 4'
  },
  {
    title: 'The Personal MBA',
    author: 'Josh Kaufman',
    description: 'Mental models and fundamentals of business. Solid, structured, no debt.',
    tag: 'Step 5'
  },
  {
    title: '$100M Offers',
    author: 'Alex Hormozi',
    description: 'How to craft offers so good people feel stupid saying no. Direct, raw, useful.',
    tag: 'Step 6 (Optional for Biz)'
  },
  {
    title: 'Why We Sleep',
    author: 'Matthew Walker',
    description: 'Understand and optimize your sleep — the most ignored part of performance.',
    tag: 'Step 7'
  },
  {
    title: 'The War of Art',
    author: 'Steven Pressfield',
    description: 'Discipline vs Resistance. Kick yourself out of stagnation.',
    tag: 'Step 8 (Optional if stuck)'
  },
  {
    title: 'Can’t Hurt Me',
    author: 'David Goggins',
    description: 'Mental toughness to the extreme. Not for comfort-seekers.',
    tag: 'Bonus: Mental Slap'
  },
  {
    title: 'Science and Practice of Strength Training',
    author: 'Zatsiorsky & Kraemer',
    description: 'Advanced book on real strength development. For lifters who want depth.',
    tag: 'Bonus: Lifting Mastery'
  }
];
</script>

<style scoped>
body {
  font-family: 'Inter', sans-serif;
}
</style>
