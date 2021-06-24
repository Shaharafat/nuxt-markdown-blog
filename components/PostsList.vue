<template>
  <ul>
    <li v-for="article in articles" :key="article.slug" class="my-4">
      <div class="flex items-start md:items-center">
        <span>
          <i class="fas fa-quote-left w-12 text-gray-500 text-2xl" />
        </span>
        <NuxtLink :to="{ name:'posts-slug', params:{slug: article.slug}}" class="font-bold text-xl  md:text-3xl text-gray-800 italic hover:underline">
          {{ article.title }}
        </NuxtLink>
      </div>
      <!-- description of 30 character -->
      <p class="text-gray-600 text-md md:text-xl ml-12">
        {{ sampleDescription(article) }}
      </p>
    </li>
  </ul>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'
import { articleInterface } from '~/utils/types'

@Component({
  name: 'ArticleList'
})
export default class ArticleList extends Vue {
  @Prop() readonly articles! : object[];

  // This computed method shows the post description
  sampleDescription (article:articleInterface) {
    console.log(this.articles)
    return article.description.slice(0, 80) + '...'
  }
}
</script>

<style scoped>
</style>
