<template>
  <article>
    {{ post.title }}

    <div class="content" v-html="post.body_html" />
    <br>
    <hr>
    saliti?
    <NuxtLink to="/dev-to">zid 9ra</NuxtLink>
    wlla
    <NuxtLink to="/">rje3</NuxtLink>
  </article>
</template>

<script>
export default {
  async asyncData({ $axios, params }) {
    const username = "moghwan";
    const singlePostUrl = `https://dev.to/api/articles/${username}/`;

    const post = await $axios.get(singlePostUrl+params.slug)
      .catch(err => console.log(err))
    return { post: post.data }
  }
}
</script>

<style>

</style>