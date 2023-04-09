<script setup>
  const story = await useStoryblok('home', {
    version: "draft", 
    resolve_relations:'featuredItems.items',
  },{
    resolveRelations: 'featuredItems.items',
  })

</script>

<template>
    <!-- <pre> {{ story }} </pre> -->
  <StoryblokComponent :blok="story.content" v-if="story"></StoryblokComponent>
</template>
