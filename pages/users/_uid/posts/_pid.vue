<template>
  <div>
    <div v-if="post" style="display: flex">
      <div style="min-width: 350px">
        <h1>{{ post.id }}</h1>
        <p>{{ post.user_id }}</p>
        <p>{{ post.title }}</p>
        <p>{{ post.body }}</p>
        <NuxtLink
          :to="`/users/${$route.params.uid}/posts/${$route.params.pid}/comments`"
          >comments</NuxtLink
        >
      </div>
      <NuxtChild style="min-width: 350px" />
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ params, $axios }) {
    let post
    if (params.uid && params.pid) {
      post = await $axios.$get(
        `https://gorest.co.in/public/v2/posts/${params.pid}`
      )
    }
    return { post }
  },
}
</script>
