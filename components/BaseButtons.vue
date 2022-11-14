<template>
  <div
    class="flex items-center gap-3"
    :class="[type, mb, noWrap ? '' : 'flex-wrap']"
  >
    <template>
      <slot name="buttons" />
    </template>
  </div>
</template>

<script>

import { defineComponent } from 'vue'


export default defineComponent({
  name: 'BaseButtons',
  props: {
    noWrap: Boolean,
    type: {
      type: String,
      default: 'justify-start',
    },
    mb: {
      type: String,
      default: '-mb-3',
    },
  },

})

</script>
