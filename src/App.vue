<template>
  <img alt="Vue logo" src="./assets/logo.png" />
  <div v-if="error">{{ error }}</div>
  <Suspense v-else>
    <template #default>
      <Users />
    </template>
    <template #fallback>
      <div>Loading users...</div>
    </template>
  </Suspense>
</template>

<script>
import Users from './components/Users.vue'
import { ref, onErrorCaptured } from 'vue'

export default {
  name: 'App',
  components: {
    Users
  },
  setup() {
    const error = ref(null)

    onErrorCaptured((e) => {
      error.value = "Something went wrong - " + e.message
    })

    return { error }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
