<template>
  <div class="mt-6">
      <div class="max-w-4xl px-10 py-6 mx-auto bg-white rounded-3xl shadow-md">
          <div class="border-b pb-2">
            <NuxtLink
              :to="{ name: 'blog-slug', params: { slug: article.slug } }"
              class="text-2xl flex font-bold text-gray-700 hover:underline relative">
              {{ article.title }}
              <DevToIcon class="absolute right-0 top-2" v-if="article.is_devto == true" />
            </NuxtLink>
          </div>
          <div class="flex items-center justify-between pt-2">
            <span class="font-light text-gray-600">{{ article.created_at }}</span>
            <div class="flex items-center justify-between">
              <a v-for="tag in article.tag_list" :key="tag.id"
                href="#"
                class="px-2 mx-1 py-1 text-sm text-gray-100 bg-gray-500 rounded hover:bg-gray-900">
                #{{ tag }}
              </a>
            </div>
          </div>
      </div>
  </div>
</template>

<script>
import DevToIcon from '@/components/icons/sites/dev-to?inline';
export default {
  components: {
    DevToIcon,
  },
  props: ['article']
}
</script>