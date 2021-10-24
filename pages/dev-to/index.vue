<template>
  <div>
    TO REMOVE
    <NuxtLink to="/">rje3</NuxtLink>
    <BlogItem v-for="post in posts" :key="post.id" :article="post"/>
  </div>
</template>

<script>
import BlogItem from '~/components/Items/BlogItem.vue'
export default {
  name: 'Blog',
  components: {
    BlogItem,
  },
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