<script setup>
defineProps({
    blok: Object,
})
</script>

<template>
    <pre>{{ blok }}</pre>
    <h2> {{ blok.title }}</h2>
</template>