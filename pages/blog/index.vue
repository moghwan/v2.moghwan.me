<template>
  <div class="w-full">
    <BlogItem v-for="post in posts" :key="post.id" :article="post"/>
  </div>
</template>

<script>
import BlogItem from '@/components/Items/BlogItem.vue'
export default {
  name: 'Blog',
  components: {
    BlogItem,
  },
  async asyncData({ $content, $axios }) {
    const articles = await $content('posts')
      .where({published: true})
      .only(['title', 'description', 'img', 'slug', 'author', 'tag_list', 'created_at'])
      .sortBy('createdAt', 'asc')
      .fetch()

    const posts = await $axios.get("https://dev.to/api/articles?username=moghwan")
      .catch(err => console.log(err))

    return {
      posts: [...posts.data, ...articles]
    }
  },
}
</script>

<style>

</style>