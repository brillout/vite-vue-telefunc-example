<script setup lang="ts">
import { ref } from 'vue'
import { computedAsync } from '@vueuse/core'
import { userInfo } from '../bff/userInfo.telefunc'

defineProps<{ msg: string }>()

const count = ref(1)

const user = computedAsync(async () => userInfo({ userId: count.value }), { message: 'Loading...' })
</script>

<template>
  <h1>{{ msg }}</h1>

  <div class="user-message">
    {{ user.message }}
  </div>

  <div class="card">
    <button type="button" @click="count++">count is {{ count }}</button>
    <p>
      Edit
      <code>components/HelloWorld.vue</code> to test HMR
    </p>
  </div>

  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/johnsoncodehk/volar" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}

.user-message {
  padding: 24px;
  background-color: #0f3d70;
  color: #ec9e5d;
  font-size: 24px;
  font-weight: 700;
  border-radius: 12px;
}
</style>
