<script setup>

  const story = await useStoryblok('portfolio', {
    version: "draft", 
    resolve_relations:'featuredItems.items',
  },{
    resolveRelations: 'featuredItems.items',
  })

  const folders = ref(['building', 'creating', 'writing'])


</script>

<template>


<StoryblokComponent :blok="story.content" v-if="story"></StoryblokComponent>
<FolderOverview 
    class="portfolio--container"
    v-for="folder in folders"
    :folder="folder"
/>

</template>

<style scoped>

</style>