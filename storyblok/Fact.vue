<script setup>
defineProps({
    blok: Object,
})
</script>

<template>
    <p>


        <span class="fact-header">
            {{ blok.factTitle }}
        </span>: 
        <span class="fact-body">
            {{ blok.description }}
        </span>
    </p>

</template>

<style scoped>
    .fact-header {
        font-weight: 700;
    }


</style>