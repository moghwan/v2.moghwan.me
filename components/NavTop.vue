<template>
  <header>
    <nav class="flex items-center justify-between">
      <div>
        <NuxtLink to="/">
          <nuxt-logo/>
        </NuxtLink>
      </div>
      <ul class="flex justify-start">
        <li class="px-2" v-for="link in links" :key="link.slug">
          <nuxt-link :to="{ name: link.slug }">
            {{ link.name }}
          </nuxt-link>
        </li>
      </ul>
    </nav>
  </header>
</template>

<script>
import NuxtLogo from '@/components/icons/NuxtLogo?inline';
export default {
  components: {
    NuxtLogo
  },
  data() {
    return {
      links: [
        // { name: 'Blog',     slug: 'blog' },
        // { name: 'Projects', slug: 'projects' },
        // { name: 'Links',    slug: 'links' },
        { name: 'About',    slug: 'about' },
      ]
    }
  }
}
</script>

<style scoped>
  .nuxt-link-active,
  .nuxt-link-exact-active {
    color: teal;
  }
</style>
