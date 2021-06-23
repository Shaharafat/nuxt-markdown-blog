<template>
  <div>{{ article.title }}</div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'
import { Context } from '@nuxt/types'

  @Component({
    name: 'Post'
  })
export default class Post extends Vue {
  // get article details
  async asyncData ({ $content, params } : Context) {
    const article = await $content('articles', params.slug).fetch()

    return { article }
  }
}
</script>

<style scoped>

</style>
