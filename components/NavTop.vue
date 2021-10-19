<template>
  <header>
    <nav class="flex items-center justify-between">
      <div>
        <NuxtLink to="/">
          <nuxt-logo/>
        </NuxtLink>
      </div>
      <ul class="flex justify-start">
        <li class="px-2">
          <NuxtLink to="/blog">Blog</NuxtLink>
        </li>
        <li class="px-2">
          <NuxtLink to="/dev-to">dev.to</NuxtLink>
        </li>
        <li class="px-2">
          <NuxtLink to="/projects">projects</NuxtLink>
        </li>
        <li class="px-2">
          <NuxtLink to="/links">links</NuxtLink>
        </li>
      </ul>
    </nav>
  </header>
</template>

<style scoped>
  .nuxt-link-active,
  .nuxt-link-exact-active {
    color: teal;
  }
</style>
