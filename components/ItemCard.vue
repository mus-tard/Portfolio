<script setup>
    const props = defineProps({ item: Object, slug: String, size: Number})

</script>

<template>
    
    <div class="container">

        <NuxtLink
            :to="'/' + slug"
            v-editable="item"
            :class="size > 2 ? 'save-space': 'take-space'"
        >
            <img
                class="image"
                :class="size === 1 ? 'single' : size === 2 ? 'double' : 'large'"
                :src="item.image.filename"
                :alt="item.image.alt"
            />
            <div class="content">
                <h3 class="title">
                {{ item.title }}
                </h3>
            </div>
        </NuxtLink>

    </div>
    
</template>

<style scoped>



    .container{
        margin: 10px 0;
        background-color: var(--primary);
    }

    .save-space{
        display: flex;
        flex-direction: row;

    }


    .take-space{
        display: flex;
        flex-direction: column;

    }

    .container a {
        text-decoration: none;
    }
    .content{
        padding: 8px;
        color: #fff;
        display: flex;
        flex-direction: column;
        justify-content: center;
    }

    .title {
        padding: 8px 0;
    }

    .single {
        object-fit:cover;
        max-inline-size: 100%;
    }
    .double {
        width: 100%;
        height: 50%;
        object-fit:cover;
    }
    .large {
        width: 150px;
        object-fit:cover;
    }
    @media only screen and (min-width: 800px){
        .container{
            flex: 1 1 300px;

        }

        .save-space{
            padding: 8px;
            flex-direction: column;
            height: 100%;
            justify-content: space-between;
        }

        .large {
            flex-basis: 300px;
            max-width: 100%;
            height: 300px;
            vertical-align: middle;
            align-self: center;
            width: unset;
            object-fit:cover;
        }

        .image {
            filter: opacity(50%) grayscale(80%);
        }
    
        .image:hover{
            filter: opacity(100%) grayscale(0%);
        }

        .content{
            text-align: center;
        }

    }

</style>