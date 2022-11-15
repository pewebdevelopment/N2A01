<script setup>
import { useStyleStore } from '@/store/style.js'
const styleStore = useStyleStore()
</script>

<template>
  <div :class="{ dark: styleStore.darkMode }">
    <div
      class="
        bg-slate-800
        flex
        justify-center
        text-white
        dark:bg-slate-800 dark:text-slate-100
      "
    >
      This is the default layout
      <div>
        <Nuxt />
      </div>
    </div>
  </div>
</template>