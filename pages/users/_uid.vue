<template>
  <div>
    <div v-if="user" style="display: flex">
      <div style="min-width: 350px">
        <h1>{{ user.name }}</h1>
        <p>{{ user.email }}</p>
        <p>{{ user.gender }}</p>
        <p>{{ user.status }}</p>
        <NuxtLink :to="`/users/${user.id}/posts`">posts</NuxtLink>
      </div>
      <NuxtChild style="min-width: 350px" />
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ params, $axios }) {
    let user
    if (params.uid) {
      user = await $axios.$get(
        `https://gorest.co.in/public/v2/users/${params.uid}`
      )
    }
    return { user }
  },
}
</script>
