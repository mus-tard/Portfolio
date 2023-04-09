<script setup>


const route = useRoute();
let child = ref(route.path.split('/')[2])
let parent = ref(route.path.split('/')[1])

const story = await useStoryblok(`portfolio/${child.value}/${route.params.slug}`, {version: "draft"})




</script>

<template>
   <div>


  
   
   <StoryblokComponent 
    :blok="story.content" 
    :child="child"
    :parent="parent"
    v-if="story"
  >
  </StoryblokComponent>

   </div>
  
</template>

