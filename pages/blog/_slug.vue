<template>
  <article>
    <img :src="post.cover_image" />
    {{ post.title }}
    <nuxt-content :document="post" />
    <div class="content" v-html="post.body_html" />
    <hr>
    saliti?
    <NuxtLink to="/blog">zid 9ra</NuxtLink>
    wlla
    <NuxtLink to="/">rje3</NuxtLink>
  </article>
</template>

<script>
export default {
  async asyncData({ $axios, $content, params }) {
    const post = await $content('posts', params.slug)
      .fetch()
      .catch(err => console.log(err))

    if(post != undefined)
      return { post }

    const username = "moghwan";
    const singlePostUrl = `https://dev.to/api/articles/${username}/`;

    const { data } = await $axios.get(singlePostUrl+params.slug)
      .catch(err => console.log(err))

    return { post: data }

  }
}
</script>

<style>

</style>