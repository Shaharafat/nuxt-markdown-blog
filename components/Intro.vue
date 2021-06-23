<template>
  <div class="mt-8 md:mt-12 lg:mt-20 grid place-items-center">
    <div class="flex flex-col items-center">
      <img src="~/assets/images/arafat.jpg" class="h-48 rounded-full border-4 border-gray-300 " alt="user">
      <div class="mt-4 flex flex-col items-center">
        <h1 class="text-2xl font-bold">
          Hello
        </h1>
        <h1 class="text-4xl font-bold text-green-500">
          I am Arafat
        </h1>
        <h2 class="text-2xl text-gray-800 text-center mt-2">
          Frontend Developer | Author | Tech Enthusiast
        </h2>
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { Component, Vue } from 'vue-property-decorator'

  @Component
export default class extends Vue {

}
</script>

<style scoped>

</style>
