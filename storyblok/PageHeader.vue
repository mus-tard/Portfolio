<script setup>
defineProps({
    blok: Object,
})
</script>
<template>
    <div class="PageHeader--container" v-editable="blok">
        
        <div class="PageHeader--title">
            <h1>{{ blok.title }}</h1>
        </div>
        
    </div>
</template>

<style scoped>
    .PageHeader--container{
        background-color: var(--primary );
        border-bottom: var(--highlight) solid 8px;
        color: var(--white);
    }
    .PageHeader--title{
        padding: 8px;
        margin: 8px 0;
    }
    @media only screen and (min-width: 500px){
        .PageHeader--container{
            padding: 32px;
        }
    }

    @media only screen and (min-width: 1024px){
        .PageHeader--title{
        max-width: 1456px;
        margin: auto;
        }
    }
</style>