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
  async asyncData({ $content, $axios, route }) {

    // TODO: filter posts by tags or type or both
    const post_type = route.query.post_type;
    const tag = route.query.tag;
    // console.info(post_type, tag)

    const articles = await $content('posts')
      // .where({published: true})
      .only(['title', 'description', 'img', 'slug', 'author', 'tag_list', 'created_at', 'is_devto'])
      .sortBy('createdAt', 'asc')
      .fetch()

    let posts = [...articles]

    try {
      const posts_devto = await $axios.get("https://dev.to/api/articles?username=moghwan")
        .catch(err => console.log(err))

      posts = [...posts, ...posts_devto.data]
    }catch{
      console.info('halo posts_devto')
    }

    return { posts }
  },
}
</script>

<style>

</style>