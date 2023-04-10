<script setup>
const storyblokApi = useStoryblokApi()
const props = defineProps({folder: String})
let content = ref(null)

const  data  = await storyblokApi.get('cdn/stories', {
  version: useRoute().query._storyblok ? "draft" : "published",
starts_with: `portfolio/`,
is_startpage: false,
})


content = data.data.stories.filter(story => {
    return story.full_slug.split('/')[1] === props.folder
  })


// https://stackoverflow.com/questions/196972/convert-string-to-title-case-with-javascript
function toTitleCase(str) {
  return str.replace(
    /\w\S*/g,
    function(txt) {
      return txt.charAt(0).toUpperCase() + txt.substr(1).toLowerCase();
    }
  );
}

</script>

<template>
<div class="FolderOverview--container" v-if="content.length>0">

  <h2>{{`${toTitleCase(props.folder)} Projects`}}</h2>
  <div class="FolderOverview--card-container">
    <ItemCard
    class="card"
    v-for="item in content"
    :key="item.uuid"
    :item="item.content"
    :slug="item.full_slug"
    :size="data.data.stories.length"
  />
  </div>

</div>


</template>

<style scoped>
  .FolderOverview--container {
    margin: 8px 0;
  }

  @media only screen and (min-width: 500px){
    .FolderOverview--container{
      padding: 32px;
    }
  }

  @media only screen and (min-width: 800px){
    .FolderOverview--card-container{

      display: flex;
      gap: 16px;
     }

  }

  @media only screen and (min-width: 1024px) {
    .FolderOverview--container{
      max-width: 1456px;
        margin: auto;
    }
  }

</style>