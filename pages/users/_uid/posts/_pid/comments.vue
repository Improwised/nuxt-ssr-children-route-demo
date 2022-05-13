<template>
  <div>
    <h1>comments</h1>
    <div style="display: flex">
      <div v-if="comments.length" style="width: 200px; padding-right: 30px">
        <p v-for="comment in comments" :key="comment.id">
          <NuxtLink
            :to="`/users/${$route.params.uid}/posts/${$route.params.pid}/comments/${comment.id}`"
          >
            {{ comment.name }}
          </NuxtLink>
        </p>
      </div>
      <div v-else>No comments found</div>
      <NuxtChild
        v-if="comments.length"
        style="width: 200px; padding-right: 30px"
      />
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ params, $axios }) {
    let comments = []
    if (params.pid) {
      comments = await $axios.$get(
        `https://gorest.co.in/public/v2/posts/${params.pid}/comments`
      )
    }
    return { comments }
  },
}
</script>
