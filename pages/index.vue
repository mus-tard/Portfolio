<script setup>
  const story = await useStoryblok('home', {
    version: useRoute().query._storyblok ? "draft" : "published",
  })

</script>

<template>
  <div class="container">
    <StoryblokComponent :blok="story.content" v-if="story"></StoryblokComponent>
  </div>

</template>

<style scoped>

</style>
