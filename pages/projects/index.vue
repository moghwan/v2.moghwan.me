<template>
  <div>
    projects index
    <NuxtLink to="/">rje3</NuxtLink>
    <div class="">
      <b>projects</b>
      <div v-for="project in projects" :key="project.id">
        {{ project.title }}
        <NuxtLink :to="{ name: 'projects-slug', params: { slug: project.slug } }">
          projectos
        </NuxtLink>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Blog',
  async asyncData({ $content, $axios }) {
    const projects = await $content('projects')
      .only(['title', 'description', 'img', 'slug', 'author'])
      .sortBy('createdAt', 'asc')
      .fetch()

    return {
      projects,
    }
  },
}
</script>

<style>

</style>