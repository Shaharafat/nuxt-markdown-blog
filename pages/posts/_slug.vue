<template>
  <div class="mt-8 md:mt-12 lg:mt-20 flex justify-center">
    <div class="w-full md:w-4/5 lg:w-3/5 xl:w-2/5">
      <div class="flex justify-end">
        <a class="px-8 py-1 bg-green-400 hover:bg-green-500 text-white text-xl cursor-pointer" @click="$router.back()">
          <i class="fas fa-arrow-left mr-2 hover:mr-4 inline-block transition" />
          Go back
        </a>
      </div>
      <div class="mt-4">
        <h1 class="text-4xl font-bold text-gray-700">
          {{ article.title }}
        </h1>
        <p class="text-gray-500 text-lg mt-2">
          Published at: {{ formatDate }}
        </p>
        <Author :author="article.author" />
      </div>
      <!-- Article Body -->
      <nuxt-content :document="article" class="mt-8" />
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import { Context } from '@nuxt/types'
import { articleInterface } from '~/utils/types'

  @Component({
    name: 'Post'
  })
export default class Post extends Vue {
  public article!: articleInterface;

  // get article details
  async asyncData ({ $content, params } : Context) {
    const article = await $content('articles', params.slug).fetch()

    return { article }
  }

  // Form the Date Value according to createdAt
  get formatDate () {
    return new Date(this.article.createdAt).toLocaleDateString()
  }

  // transition
  transition () {
    return 'slide-bottom'
  }
}
</script>

<style scoped>

</style>
