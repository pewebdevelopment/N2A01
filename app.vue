<script setup>
import { onMounted, ref } from 'vue'
import { useStyleStore } from '@/stores/style.js'
import { darkModeKey, styleKey } from '@/configs/config'

// import '@/assets/css/main.css'

const styleStore = useStyleStore()
const loading = ref(true)

onMounted(() => {
  styleStore.setStyle(localStorage[styleKey] ?? 'basic')
  /* Dark mode */
  if (
    (!localStorage[darkModeKey] &&
      window.matchMedia('(prefers-color-scheme: dark)').matches) ||
    localStorage[darkModeKey] === '1'
  ) {
    styleStore.setDarkMode()
  }
  loading.value = false
})
</script>


<template>
  <div>
    <Nuxt />
  </div>
</template>