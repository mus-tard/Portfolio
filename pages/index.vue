<script setup>
  const story = await useStoryblok('home', {
    version: "draft"
  })

</script>

<template>
    <!-- <pre> {{ story }} </pre> -->
  <StoryblokComponent :blok="story.content" v-if="story"></StoryblokComponent>
</template>
