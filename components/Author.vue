<template>
  <div class="flex justify-start items-center mt-2">
    <div class="mr-2">
      <img :src="author.image" alt="author" class="w-16 border-2 rounded-full border-gray-400">
    </div>
    <div>
      <h1 class="text-green-500 font-bold text-xl">
        {{ author.name }}
      </h1>
      <p class="text-gray-500 text-lg">
        {{ author.designation }}
      </p>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Prop, Vue } from 'vue-property-decorator'

@Component({
  name: 'Author'
})
export default class Author extends Vue {
@Prop() readonly author!:object;
}
</script>

<style scoped>

</style>
