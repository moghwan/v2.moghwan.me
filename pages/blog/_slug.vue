<template>
  <article>
    <h2>table of content</h2>
    <nav>
      <ul>
        <li v-for="link of post.toc" :key="link.id">
          <NuxtLink :to="`#${link.id}`">{{ link.text }}</NuxtLink>
        </li>
      </ul>
    </nav>
    <img :src="post.cover_image" :alt="post.alt" />
    <nuxt-content :document="post" />
    <hr>
    saliti?
    <NuxtLink to="/blog">zid 9ra</NuxtLink>
    wlla
    <NuxtLink to="/">rje3</NuxtLink>
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const post = await $content('posts', params.slug).fetch()
    return { post }
  }
}
</script>

<style>

</style>