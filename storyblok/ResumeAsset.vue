<script setup>
defineProps({
    blok: Object,
})
</script>

<template>

<!-- <pre>{{ blok }}</pre> -->

    <div class="main-container">
        <div class="res-container">
            <h2 class="res-title">{{blok.resumename1}}</h2>
            <div class="res-image">
                <img 
                    :src="blok.preview1.filename" 
                    :alt="blok.preview1.alt"
                /> 
            </div>
            <div class="res-btn">
                <a target="_blank" :href="blok.download1.filename" class="download">
                    Download
                </a>
            </div>
        </div>
        <div class="res-container">
            <h2 class="res-title">{{blok.resumename2}}</h2>
            <div class="res-image">
                <img 
                    :src="blok.preview2.filename" 
                    :alt="blok.preview2.alt"
                /> 
            </div>
            <div class="res-btn">
                <a target="_blank" :href="blok.download2.filename" class="download">
                    Download
                </a>
            </div>
        </div> 
    </div>

</template>

<style scoped>
    .main-container {
        display: flex;
        flex-direction:column-reverse;
        
    }

    .res-title{
        padding: 8px;
        color: var(--white);
    }

    .res-image {
        display: flex;
        justify-content: center;
    }
    .res-image img{
        max-inline-size: 100%;
        object-fit: cover;
        object-position: top;
        max-block-size: 300px;
    }

    .res-btn{
        display: flex;
        gap: 8px;
        padding: 8px;
        justify-content: center;
    }

    .res-btn a {
        width: 100%;
        padding: 16px 8px;
        text-align: center;
    }

    .download {
        background-color: var(--white);
        color: var(--black);
        text-decoration: none;
    }


    @media only screen and (min-width: 500px){
        .main-container{
            padding: 0 32px;
        }
        .res-image img{
        max-block-size: 500px;
        }
        .res-btn a {
            width: 400px;
        }
    }
    @media only screen and (min-width: 1024px){

        .res-container{
            width: 100%;
            max-width: 1456px;
            margin: auto;
        }

        .res-image img{
        max-block-size: 800px;
        }
    }
</style>