<template>
  <div>
    dev.to index
    <NuxtLink to="/">rje3</NuxtLink>
    <div class="">
      <b>posts</b>
      <div v-for="post in posts" :key="post.id">
        {{ post.title }}
        <NuxtLink :to="{ name: 'dev-to-slug', params: { slug: post.slug } }">
          devtos
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Blog',
  async asyncData({ $content, $axios }) {
    const posts = await $axios.get("https://dev.to/api/articles?username=moghwan")
      .catch(err => console.log(err))

    return {
      posts: posts.data,
    }
  },
}
</script>

<style>

</style>