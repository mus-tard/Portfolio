<script setup>
defineProps({
    blok: Object,
})
</script>
<template>
    <div class="Page--container">

        <!-- <pre>{{ blok }}</pre> -->
        <StoryblokComponent
            v-for="blok in blok.body"
            :key="blok._uuid"
            :blok="blok"
        ></StoryblokComponent>

    </div>
</template>
<style scoped>
    .Page--container{
        display:flex;
        flex-direction: column;
        justify-content: flex-start;
    }
    
</style>