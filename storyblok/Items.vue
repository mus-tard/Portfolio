<script setup>
const props = defineProps({
    blok: Object,
    parent: String,
    child: String
});



// https://stackoverflow.com/questions/196972/convert-string-to-title-case-with-javascript
function toTitleCase(str) {
  return str.replace(
    /\w\S*/g,
    function(txt) {
      return txt.charAt(0).toUpperCase() + txt.substr(1).toLowerCase();
    }
  );
}
const customTitle = `${toTitleCase(props.child)} Project:  ${props.blok.title} `

const newDate = function getDateString (inputDate) {
    // https://stackoverflow.com/questions/948532/how-to-convert-a-date-to-utc
    const date = new Date(inputDate);
    const options = { year: 'numeric', month: 'long' };
    return date.toLocaleDateString(undefined, options)
}



</script>
<template>
    <div>



        <p class="breadCrumbs"><NuxtLink class="links" :to="`/`">Home</NuxtLink> > <NuxtLink class="links"  :to="`/${toTitleCase(parent)}`">{{ toTitleCase(parent) }}</NuxtLink></p>
        
        <div class="PageHeader--container">
        
            <div class="PageHeader--title">
                <h1 class="">{{ customTitle || "New Item"}}</h1>
            </div>
            <p class="description">{{ blok.shortDescription || "Lorem ipsum dolor, sit amet consectetur adipisicing elit. Laborum alias error esse nobis suscipit illum molestiae blanditiis vel sunt, a eius ad mollitia veniam necessitatibus adipisci, eum ab. Dolores, natus." }}</p>
            <div v-if="blok.startdate"><p>📅 {{ `${newDate(blok.startdate)} ${blok.enddate === blok.startdate ? "" : blok.enddate ? " - " + newDate(blok.enddate) :  "- Ongoing"}`  }}</p></div>
        </div>

        <div class="intro-image"><img :src="blok.image?.filename || 'https://picsum.photos/300/175'" :alt="blok.image?.alt" /></div>


    </div>
    
</template>

<style scoped>

    .breadCrumbs{
        background-color: var(--black);
        color: var(--white);
        padding: 20px;
    }

    .links{
        text-decoration:underline;
        color: var(--white)
    }
    
    .PageHeader--container{
        background-color: var(--primary );
        border-bottom: var(--highlight) solid 8px;
        color: var(--white);
    }
    .PageHeader--title{
        padding: 8px;
        margin: 8px 0;
    }

    .description{
        padding: 16px 0;
    }

    .intro-image img{
        width: 100%;
    }

    .involvement li{

	    list-style:disc;

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