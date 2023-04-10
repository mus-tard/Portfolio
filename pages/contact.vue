<script setup>
  const story = await useStoryblok('contact', {
    version: useRoute().query._storyblok ? "draft" : "published"
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