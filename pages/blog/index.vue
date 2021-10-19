<template>
  <div>
    blog index
    <NuxtLink to="/">rje3</NuxtLink>
    <div class="">
      <b>articles</b>
      <div v-for="article in articles" :key="article.id">
        {{ article.title }}
        <!-- {{ article }} -->
        <NuxtLink :to="{ name: 'blog-slug', params: { slug: article.slug } }">
          linkos
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Blog',
  async asyncData({ $content, $axios }) {
    const articles = await $content('posts')
      .only(['title', 'description', 'img', 'slug', 'author'])
      .sortBy('createdAt', 'asc')
      .fetch()

    return {
      articles,
    }
  },
}
</script>

<style>

</style>