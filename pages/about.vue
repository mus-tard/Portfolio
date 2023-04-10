<script setup>
  const story = await useStoryblok('about', {
    version: "draft"
  })

</script>
<template>
        <div class="container">
            <!-- <pre>{{ story }}</pre> -->
            <StoryblokComponent 
                :blok="story.content" 
                v-if="story"
            >
            </StoryblokComponent>
        </div>
</template>

<style scoped>
  .container{
    background-color: var(--primary);
  }
</style>