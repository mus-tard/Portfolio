<script setup>
defineProps({
    blok: Object,
})
</script>

<template>

    <!-- <pre>{{ blok }}</pre> -->
    <div class="container">
        <StoryblokComponent
                v-for="blok in blok.container"
                :key="blok._uuid"
                :blok="blok"
        >
        </StoryblokComponent>

    </div>

</template>

<style scoped>
    .container {
        display: flex;
        flex-direction: column;
    }
    @media only screen and (min-width: 1024px){
        .container{
            height: 100%;
        }

    }
</style>