<template>
  <div>
    <h1>posts</h1>
    <div style="display: flex">
      <div v-if="posts.length" style="width: 200px; padding-right: 30px">
        <p v-for="post in posts" :key="post.id">
          <NuxtLink :to="`/users/${$route.params.uid}/posts/${post.id}`">
            {{ post.title }}
          </NuxtLink>
        </p>
      </div>
      <div v-else>No post found</div>
      <NuxtChild
        v-if="posts.length"
        style="width: 200px; padding-right: 30px"
      />
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ params, $axios }) {
    const posts = await $axios.$get(
      `https://gorest.co.in/public/v2/users/${params.uid}/posts`
    )
    return { posts }
  },
}
</script>
