<script setup>
defineProps({
    blok: Object,
})
</script>

<template>

    <div class="container">
        <StoryblokComponent
            v-for="blok in blok.facts"
            :key="blok._uuid"
            :blok="blok"
            class="facts"
        ></StoryblokComponent>
    </div>    
        
</template>

<style scoped>
    .container {
        background-color: var(--primary);
        color: var(--white);
        padding: 8px;
    }

   @media only screen and (min-width: 500px){
        .container{
            padding: 32px;
        }
    }
    @media only screen and (min-width: 1024px){
        .container{
            padding: 64px 64px;
            flex-direction: column;
            justify-content: center;
        }


    }

    
</style>