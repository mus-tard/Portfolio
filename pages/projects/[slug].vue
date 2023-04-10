<script setup>
const route = useRoute();
const story = await useStoryblok(`projects/${route.params.slug}`, {
   version: useRoute().query._storyblok ? "draft" : "published",
   })
</script>

<template>
   <StoryblokComponent :blok="story.content" v-if="story"></StoryblokComponent>
</template>