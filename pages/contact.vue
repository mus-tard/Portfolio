<script setup>
  const story = await useStoryblok('contact', {
    version: useRoute().query._storyblok ? "draft" : "published"
  })

</script>
<template>
        <div class="container">
            <!-- <pre>{{ story }}</pre> -->
            <div class="deets">
              <p><span class="bold">Contact</span> - 514-714-6090</p>
              <p><span class="bold">Email</span> - contact@kevd.design</p>

          </div>
            <StoryblokComponent 
                :blok="story.content" 
                v-if="story"
            >
            </StoryblokComponent>
        </div>
</template>

<style scoped>

</style>