<!-- eslint-disable vue/no-lone-template -->
<script setup>
import { computed } from 'vue'
import { mdiForwardburger, mdiBackburger, mdiMenu } from '@mdi/js'
// import { useRouter } from "vue-router";

import menuAside from '@/configs/menuAside.js'
import menuNavBar from '@/configs/menuNavBar.js'
import { useMainStore } from '@/store/main.js'
import { useLayoutStore } from '@/store/layout.js'
import { useStyleStore } from '@/store/style.js'
import BaseIcon from '@/components/BaseIcon.vue'
import FormControl from '@/components/FormControl.vue'
import NavBar from '@/components/NavBar.vue'
import NavBarItemPlain from '@/components/NavBarItemPlain.vue'
import FooterBar from '@/components/FooterBar.vue'
// import PremAsideMenu from '@/components/prem/AsideMenu.vue'

useMainStore().setUser({
  name: 'Zen Athang',
  email: 'john@example.com',
  avatar:
    'https://avatars.dicebear.com/api/avataaars/example.svg?options[top][]=shortHair&options[accessoriesChance]=93',
})

const layoutAsidePadding = computed(() =>
  layoutStore.isAsideLgActive ? 'lg:pl-20' : 'xl:pl-20'
)

const styleStore = useStyleStore()

const layoutStore = useLayoutStore()

// const router = useRouter();

const router = this.$nuxt._router // This is not working

// this.$nuxt.$route.name // returns 'about-us'
// this.$nuxt.$route.path // returns '/about-us'

// You can also access the route and router object from the global $nuxt object this way

//  this.$nuxt._route
//  this.$nuxt._router

router.beforeEach(() => {
  layoutStore.isAsideMobileExpanded = false
})

const menuClick = (event, item) => {
  if (item.isToggleLightDark) {
    styleStore.setDarkMode()
  }

  if (item.isLogout) {
    //
  }
}
</script>

<template>
  <div>
    <div
      :class="{
        dark: styleStore.darkMode,
        'overflow-hidden lg:overflow-visible':
          layoutStore.isAsideMobileExpanded,
      }"
    >
      <div
        :class="[
          layoutAsidePadding,
          { 'ml-60 lg:ml-0': layoutStore.isAsideMobileExpanded },
        ]"
        class="
          pt-14
          min-h-screen
          w-screen
          transition-position
          lg:w-auto
          bg-gray-50
          dark:bg-slate-800 dark:text-slate-100
        "
      >
        <NavBar
          :menu="menuNavBar"
          :class="[
            layoutAsidePadding,
            { 'ml-60 lg:ml-0': layoutStore.isAsideMobileExpanded },
          ]"
          @menu-click="menuClick"
        >
          <NavBarItemPlain
            display="flex lg:hidden"
            @click.prevent="layoutStore.asideMobileToggle()"
          >
            <BaseIcon
              :path="
                layoutStore.isAsideMobileExpanded
                  ? mdiBackburger
                  : mdiForwardburger
              "
              size="24"
            />
          </NavBarItemPlain>
          <NavBarItemPlain
            display="hidden lg:flex xl:hidden"
            @click.prevent="layoutStore.asideLgToggle()"
          >
            <BaseIcon
              :path="layoutStore.isAsideLgActive ? mdiBackburger : mdiMenu"
              size="24"
            />
          </NavBarItemPlain>
          <NavBarItemPlain use-margin>
            <FormControl
              placeholder="Search (ctrl+k)"
              ctrl-k-focus
              transparent
              borderless
            />
          </NavBarItemPlain>
        </NavBar>

        <AsideMenu :menu="menuAside" @menu-click="menuClick" />

        <!-- Use the Nuxt tag in Nuxt 2 Instead of the slot Tag -->
        // eslint-disable-next-line vue/no-lone-template

        <div>
          <Nuxt />
        </div>

        <FooterBar>
          <a href="#" target="_blank" class="text-blue-800"> Photon Ecademy </a>
        </FooterBar>
      </div>
    </div>
  </div>
</template>
