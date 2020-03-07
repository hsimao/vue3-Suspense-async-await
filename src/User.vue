<template>
  <div>Hello from User Component</div>
</template>

<script>
import { ref } from 'vue'

export default {
  async setup() {
    const promise = new Promise((resolve, reject) => {
      setTimeout(() => {
        reject('Success')
      }, 2000)
    })

    const user = await promise
    return { user }
  }
}
</script>

<style scoped></style>
