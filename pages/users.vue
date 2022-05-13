<template>
  <div>
    <h1>Users</h1>
    <div style="display: flex">
      <div style="min-width: 350px">
        <div v-for="user in users" :key="user.id">
          <NuxtLink :to="`/users/${user.id}`">
            {{ user.name }}
          </NuxtLink>
        </div>
      </div>
      <NuxtChild v-if="users.length" style="min-width: 350px" />
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ params, $axios }) {
    const users = await $axios.$get(`https://gorest.co.in/public/v2/users`)
    return { users }
  },
}
</script>
