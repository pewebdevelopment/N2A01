<script setup>
import { reactive } from 'vue'
import { mdiAccount, mdiAsterisk } from '@mdi/js'

import VueRouter from 'vue-router'
// import { useRouter } from "vue-router";

const form = reactive({
  login: 'john.doe',
  pass: 'highly-secure-password-fYjUw-',
  remember: true,
})
const router = VueRouter

// Vue.use(VueRouter);
const submit = () => {
  router.push('/dashboard')
}
</script>

<template>
  <div>
    <SectionFullScreen v-slot="{ cardClass }" bg="purplePink">
      <CardBox :class="cardClass" is-form @submit.prevent="submit">
        <FormField label="Login" help="Please enter your login">
          <FormControl
            v-model="form.login"
            :icon="mdiAccount"
            name="login"
            autocomplete="username"
          />
        </FormField>

        <FormField label="Password" help="Please enter your password">
          <FormControl
            v-model="form.pass"
            :icon="mdiAsterisk"
            type="password"
            name="password"
            autocomplete="current-password"
          />
        </FormField>

        <FormCheckRadio
          v-model="form.remember"
          name="remember"
          label="Remember"
          :input-value="true"
        />

        <template #footer>
          <BaseButtons>
            <template #buttons>
              <BaseButton type="submit" color="info" label="Login" />
 
              <BaseButton to="/dashboard" color="info" outline label="Back" />
            </template>
          </BaseButtons>
        </template>
      </CardBox>
    </SectionFullScreen>
  </div>
</template>
