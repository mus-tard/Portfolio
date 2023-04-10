<script setup>
  const story = await useStoryblok('resume', {
    version: useRoute().query._storyblok ? "draft" : "published"
  })

</script>
<template>

   <!-- <pre> {{ story }}</pre> -->
    <div class="container">
        <StoryblokComponent :blok="story.content" v-if="story"></StoryblokComponent>
    </div>
</template>

<style scoped>

    .container{
        background-color: var(--primary);
        
    }

</style>