<script setup>
defineProps({
    blok: Object,
})
</script>
<template>
    <div class="Hero--container" v-editable="blok">
        <div class="Hero--content">
            <div class="Hero--display-text"> {{ blok.heading }}</div>
            <p class="Hero--paragraph-text"> {{ blok.subheading }}</p>
            <NuxtLink to="/portfolio" class="Hero--cta">
                 {{ blok.cta }}
            </NuxtLink>
        </div>
    </div>
    
</template>

<style scoped>
.Hero--container {
    padding:8px;
}

.Hero--content{
    display: flex;
    flex-direction: column;
    gap: 8px;
}

.Hero--display-text{
    font-size: var(--mobile-display-text);
    line-height: 1.2;
}

.Hero--cta{
    width: 100%;
    text-align: center;
    cursor: pointer;
    padding: 8px;
    text-decoration: none;
}

@media only screen and (min-width: 500px){

    .Hero--container{
        padding: 48px;
    }
    .Hero--content{
        max-width: 500px;
        margin: auto;
        
    }

    .Hero--display-text{
    font-size: var(--tablet-display-text);
    }

}

@media only screen and (min-width: 1024px){
    .Hero--container{
        padding: 256px 40px;
    }
    .Hero--content{
        max-width: 1456px;
        margin: auto;
    }
    .Hero--display-text{
    font-size: var(--desktop-display-text);
    }
    .Hero--cta{
        width: 344px;
    }

}

</style>