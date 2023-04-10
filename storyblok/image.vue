<script setup>
defineProps({
    blok: Object,
})
</script>

<template>
    <div class="container">
        <img :src="blok.image.filename" :alt="blok.image.alt"/>
    </div>
</template>

<style scoped>
    .container {
            display: flex;
            
        }

        img {
            object-fit: cover;
            object-position: top;
            max-inline-size: 100%;
        }
    @media only screen and (min-width: 500px) {
        
        img {

        }
    }
    @media only screen and (min-width: 1024px) {
        .container {
            display: flex;
            justify-content: center;
            background-color: var(--primary);
        }
        img {
            max-inline-size: 600px;
            max-block-size: 100%;
        }
    }
    @media only screen and (min-width: 1400px) {
        img {
            max-inline-size: 800px;
            max-block-size: 100%;
        }
    }

</style>