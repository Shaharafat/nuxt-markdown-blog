<template>
  <ul>
    <li v-for="article in articles" :key="article.slug" class="my-4">
      <div class="flex items-start md:items-center">
        <img src="~/assets/images/pen.jpg" alt="pen icon" class="w-8 mr-2">
        <NuxtLink :to="{ name:'posts-slug', params:{slug: article.slug}}" class="font-bold text-3xl text-gray-800 italic hover:underline">
          {{ article.title }}
        </NuxtLink>
      </div>
      <!-- description of 30 character -->
      <p class="text-gray-600 text-xl ml-10">
        {{ article.description.slice(0,30) }}
      </p>
    </li>
  </ul>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component({
  name: 'ArticleList'
})
export default class ArticleList extends Vue {
  @Prop() readonly articles! : object[];
}
</script>

<style scoped>

</style>
