<script setup>
defineProps({
    blok: Object,
})
</script>

<template>
<div class="container"> 
    <!-- <pre>{{ blok }}</pre> -->

    <StoryblokComponent
            
            v-for="blok in blok.columns"
            :key="blok._uuid"
            :blok="blok"
        ></StoryblokComponent>

</div>

</template>

<style scoped>
    .container{ 
        display: flex;
        flex-direction: column;
    }

    @media only screen and (min-width: 1024px){
        .container{
            flex-direction: row;
            height: 1500px;
            justify-content: center;
            max-width: 1456px;
            margin: auto;
           
        }
    }
</style>