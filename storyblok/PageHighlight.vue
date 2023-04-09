<script setup>
defineProps({
    blok: Object,
})


const colorsBkg = ["var(--white)", "var(--primary)", ]
const colorsText = ["var(--black)", "var(--white)",]
const colorsBtn = ["var(--primary)", "var(--white)", ]
const colorsBtnText = ["var(--white)", "var(--black)",]
</script>

<template>


<div class="PageHighlight--container"  v-editable="blok">
    
    
    
    <div 
    v-for="(page, index) in blok.SiteContents"
    v-bind:key="index" 
    v-bind:style="{backgroundColor: colorsBkg[index % 2]}"
    class="PageHighlight--highlight"
    >
    <div class="PageHighlight--container-content">
        <div
        v-bind:style="{color: colorsText[index % 2]}"
        >
        
            <div class="PageHighlight--title">
            <h2>{{ page.name }}</h2>
            </div>
            <div class="PageHighlight--description">
            <p>{{ page.introduction }}</p>
            </div>
        </div>
        
        <NuxtLink
            v-bind:style="{backgroundColor: colorsBtn[index % 2], color: colorsBtnText[index % 2]}"
            class="PageHighlight--button"
            :to="`/${page.slug}`"
        >
            {{ page.cta }}

            
    </NuxtLink>
    </div>
    </div>
       
</div>


</template>

<style scoped>

    .PageHighlight--container{
        display: flex;
        flex-direction: column;
    }

    .PageHighlight--highlight{
        padding: 8px;
        flex: 1 1 auto;
        display: flex;
        align-items: center;

    }

    .PageHighlight--container-content{
        display: flex;
        flex-direction: column;
        gap: 8px;
    }

    

    .PageHighlight--title{
        margin: 8px 0;
    }

    .PageHighlight--button{
        padding: 16px;
        display: flex;
        justify-content: center;
        text-decoration: none;
    }
    
    @media only screen and (min-width: 500px){
        
        .PageHighlight--highlight{
            width: 100%;
            display: flex; 
            justify-content: center;
            align-items: center;
        }
        

        .PageHighlight--container-content{
            max-width: 500px;
            margin:auto;
            padding: 32px;
        }
    }

    @media only screen and (min-width: 1024px) {
        .PageHighlight--container{
            display: flex;
            flex-direction: row;

        }
        

        .PageHighlight--container-content{
            max-width: unset;
        }
    }

</style>