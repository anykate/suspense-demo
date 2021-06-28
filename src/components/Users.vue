<template>
  <div v-for="user in users" :key="user.id">
    {{ user.first_name }} {{ user.last_name }}
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  name: "Users",

  async setup() {
    const users = ref(null)

    const usersResponse = await fetch('https://reqres.i/api/users?delay=3')
    const userData = await usersResponse.json()
    users.value = await userData.data

    return { users, }
  }
}
</script>

<style scoped>
</style>