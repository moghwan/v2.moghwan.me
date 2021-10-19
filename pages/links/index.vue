<template>
  <div>
    links index
    <NuxtLink to="/">rje3</NuxtLink>
    <div class="">
      <b>links</b>
      <div v-for="link in links" :key="link.id">
        {{ link.title }}
        <NuxtLink :to="{ name: 'links-slug', params: { slug: link.slug } }">
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
    const links = await $content('links')
      .only(['title', 'description', 'img', 'slug', 'author'])
      .sortBy('createdAt', 'asc')
      .fetch()

    return {
      links,
    }
  },
}
</script>

<style>

</style>