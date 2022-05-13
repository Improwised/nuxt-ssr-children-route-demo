<template>
  <div>
    <div v-if="comment" style="display: flex">
      <div style="min-width: 350px">
        <h1>{{ comment.id }}</h1>
        <p>{{ comment.post_id }}</p>
        <p>{{ comment.email }}</p>
        <p>{{ comment.name }}</p>
        <p>{{ comment.body }}</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ params, $axios }) {
    let comment
    if (params.cid) {
      comment = await $axios.$get(
        `https://gorest.co.in/public/v2/comments/${params.cid}`
      )
    }
    return { comment }
  },
}
</script>
