<script setup>
import { ref, onMounted } from 'vue'
import { PhSun, PhMoon } from '@phosphor-icons/vue'

const isDark = ref(false)

onMounted(() => {
  // load saved theme
  if (localStorage.getItem('theme') === 'dark') {
    isDark.value = true
    document.documentElement.classList.add('dark')
  }
})

const toggleTheme = () => {
  isDark.value = !isDark.value

  if (isDark.value) {
    document.documentElement.classList.add('dark')
    localStorage.setItem('theme', 'dark')
  } else {
    document.documentElement.classList.remove('dark')
    localStorage.setItem('theme', 'light')
  }
}
</script>

<template>
  <button
    @click="toggleTheme"
    class="px-4 py-2 bg-gray-200 dark:bg-gray-700 dark:text-white rounded shadow cursor-pointer dark-transition"
  >
  <PhSun v-if="isDark" :size="25" />
  <PhMoon v-else :size="25" />
  </button>
</template>
