<script setup>
defineProps({
    blok: Object,
});
</script>
<template>
    <div v-editable="blok">
        <div v-for="item in blok.items" :key="item._uid">
            <NuxtLink
                :to="{ name: 'items-slug', params: { slug: item.slug }}"
            >
            <h3>{{ item.content.title }}</h3>
            <img 
                width="300px"
                :src="item.content.image?.filename"
                :alt="item.content.image?.alt"
            />
            </NuxtLink>
        
        </div>
    </div>

</template>

