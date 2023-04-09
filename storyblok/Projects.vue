<script setup>
defineProps({
    blok: Object,
})
</script>

<template>

    <h1>{{ blok.name }}</h1>
    <NuxtLink :to="{ name: 'index' }">Go back</NuxtLink>
    
    <p>{{ blok.description }}</p>
    </template>