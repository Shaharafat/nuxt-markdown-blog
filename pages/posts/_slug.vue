<template>
  <div class="mt-8 md:mt-12 lg:mt-20 flex justify-center">
    <div class="w-full sm:w-4/5 md:w-3/5 lg:2/6 px-4 md:px-4">
      <div class="flex justify-end">
        <!-- Go Back Button -->
        <NuxtLink id="back-button" :to="previousPath" class="px-8 py-1 shadow-md bg-green-400 hover:bg-green-500 text-white text-xl cursor-pointer">
          <span class=" inline-block mr-2">
            <i class="fas fa-arrow-left " />
          </span>
          Go back
        </NuxtLink>
      </div>

      <div class="mt-4">
        <h1 class="text-4xl font-bold text-gray-700">
          {{ article.title }}
        </h1>
        <p class="text-gray-500 text-lg mt-2">
          Published at: {{ formatDate }}
        </p>
        <!-- Author Image and Designation -->
        <Author :author="article.author" />
      </div>

      <!-- Article Body -->
      <nuxt-content :document="article" class="mt-8 pb-10 prose prose-sm sm:prose lg:prose-lg xl:prose-2xl" />
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
  // public previousPath: string = this.$nuxt.context.from.path || '/';

  // get article details
  async asyncData ({ $content, params } : Context) {
    const article = await $content('articles', params.slug).fetch()
    return { article }
  }

  // Form the Date Value according to createdAt
  get formatDate () {
    return new Date(this.article.createdAt).toLocaleDateString()
  }

  // get the previous path
  get previousPath () {
    const { from } = this.$nuxt.context

    return from ? from.path : '/'
  }

  // transition
  transition () {
    return 'slide-bottom'
  }
}
</script>

<style scoped>
#back-button:hover span{
  transform: translateX(-.5rem);
  transition: transform 300ms ease-in;
}
</style>
