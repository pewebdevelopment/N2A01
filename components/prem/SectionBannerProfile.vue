<script setup>
import { mdiGithub } from "@mdi/js";
import BaseButton from "@/components/BaseButton.vue";
import SectionBanner from "@/components/SectionBanner.vue";
</script>

<template>
  <SectionBanner
    class="bg-gradient-to-tr from-cyan-400 via-violet-400 to-purple-500"
  >
    <h1 class="text-3xl text-white mb-6">
      Like the project? Please star on <b>GitHub</b> ;-)
    </h1>
    <div>
      <BaseButton
        href="https://github.com/justboil/admin-one-vue-tailwind"
        :icon="mdiGithub"
        label="GitHub"
        target="_blank"
        rounded-full
      />
    </div>
  </SectionBanner>
</template>
