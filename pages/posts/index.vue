<template>
  <div class="mt-8 md:mt-12 lg:mt-20 flex justify-center">
    <div class="w-full sm:w-4/5 md:w-3/5 lg:2/6 px-4 mt-4 ">
      <div class="flex justify-between items-center">
        <h3 class="text-green-500 text-3xl font-bold">
          All Blogs
        </h3>
        <!-- Home Button -->
        <NuxtLink to="/">
          <span class="text-green-400 text-2xl">
            <i class="fas fa-home" />
          </span>
        </NuxtLink>
      </div>
      <!-- All Article list -->
      <PostsList :articles="allArticles" />
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import { Context } from '@nuxt/types'

  @Component({
    name: 'Posts'
  })
export default class Posts extends Vue {
  public head ():object {
    return {
      title: 'All Posts | Markdown Blog'
    }
  }

  async asyncData ({ $content }:Context) {
    const allArticles = await $content('articles').sortBy('createdAt', 'desc').fetch()

    return { allArticles }
  }

  // transition
  transition () {
    return 'slide-bottom'
  }
}

</script>

<style scoped>

</style>
