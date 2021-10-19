<template>
  <article>
    <h2>table of content</h2>
    <nav>
      <ul>
        <li v-for="project of post.toc" :key="project.id">
          <NuxtLink :to="`#${project.id}`">{{ project.text }}</NuxtLink>
        </li>
      </ul>
    </nav>
    <img :src="post.cover_image" :alt="post.alt" />
    <nuxt-content :document="post" />
    <hr>
    saliti?
    <NuxtLink to="/projects">zid 9ra</NuxtLink>
    wlla
    <NuxtLink to="/">rje3</NuxtLink>
  </article>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const post = await $content('projects', params.slug).fetch()
    return { post }
  }
}
</script>

<style>

</style>