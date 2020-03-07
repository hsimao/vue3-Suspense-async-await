<template>
  <div>
    <div v-if="error">Error loading component{{ error }}</div>
    <Suspense>
      <template #default>
        <User />
      </template>
      <template #fallback>
        <div>Loading...</div>
      </template>
    </Suspense>

    <h1>Hello Vue 3!</h1>
    <button @click="inc">Clicked {{ count }} times.</button>
  </div>
</template>

<script>
import { ref, onErrorCaptured } from 'vue'
import User from './User.vue'

export default {
  components: {
    User
  },
  setup() {
    // 監聽異步 error
    const error = ref(null)
    onErrorCaptured(e => {
      error.value = e
      return true
    })

    const count = ref(0)
    const inc = () => {
      count.value++
    }

    return {
      count,
      inc,
      error
    }
  }
}
</script>

<style scoped>
img {
  width: 200px;
}
h1 {
  font-family: Arial, Helvetica, sans-serif;
}
</style>
