<script setup>
defineProps({
    blok: Object,
})
</script>

<template>
    <div class="container">
        <h2>{{ blok.descriptionTitle }}</h2>
        <p>{{ blok.description }}</p>
    </div>

</template>

<style scoped>
    .container {
        padding: 8px;
        color: var(--white);
    }

    @media only screen and (min-width: 500px){
        .container{
            padding: 32px;
        }
    }
    @media only screen and (min-width: 1024px){
        .container{

            max-width: 1456px;
            margin: auto;
            
            padding: 64px 64px;
            flex-direction: column;
            justify-content: center;
            height: 100%;
        }

    }
</style>