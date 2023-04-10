<script setup>
  const story = await useStoryblok('contact', {
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
            <ContactForm />
        </div>
</template>

<style scoped>

</style>