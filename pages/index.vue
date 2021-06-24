<template>
  <div class="grid grid-cols-1 lg:grid-cols-2">
    <Intro />
    <!-- Recent Posts Section Start -->
    <div class="min-h-screen flex flex-col items-center justify-center w-full md:w-3/5 lg:w-2/3 ">
      <div class="px-4 mt-4">
        <h3 class="text-green-500 text-3xl ml-12 font-bold">
          Recent Posts
        </h3>
        <!-- List of Recent Posts (MAX: 5) -->
        <PostsList :articles="recentArticles" />
      </div>
      <!-- Recent Post Section End -->
      <div class="flex justify-center my-8">
        <NuxtLink to="/posts" class="bg-green-500 hover:bg-green-600 px-12 py-3 text-white shadow-md rounded-md">
          More Blogs
        </NuxtLink>
      </div>
    </div>
    <!-- Recent Posts Section End -->
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'nuxt-property-decorator'
import { Context } from '@nuxt/types'

@Component({
  name: 'Index'
})
export default class Index extends Vue {
  public head (): object {
    return {
      title: 'Home | Markdown Blog'
    }
  }

  async asyncData ({ $content }:Context) {
    const recentArticles = await $content('articles').limit(5).sortBy('createdAt', 'desc').fetch()

    return { recentArticles }
  }

  // transition
  transition () {
    return 'slide-bottom'
  }
}
</script>

<style scoped>
</style>
