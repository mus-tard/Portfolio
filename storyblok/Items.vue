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

         <!-- <pre>{{ blok }}</pre> -->
         

        <p class="breadCrumbs"><NuxtLink class="links" :to="`/`">Home</NuxtLink> > <NuxtLink class="links"  :to="`/${toTitleCase(parent)}`">{{ toTitleCase(parent) }}</NuxtLink></p>
        
        <div class="PageHeader--container">
            <div class="intro-image"><img :src="blok.image?.filename || 'https://picsum.photos/300/175'" :alt="blok.image?.alt" /></div>

            <div class="intro-content">
                <div class="PageHeader--title">
                    <h1 class="">{{ customTitle || "New Item"}}</h1>
                </div>
                <p class="description">{{ blok.shortDescription || "Lorem ipsum dolor, sit amet consectetur adipisicing elit. Laborum alias error esse nobis suscipit illum molestiae blanditiis vel sunt, a eius ad mollitia veniam necessitatibus adipisci, eum ab. Dolores, natus." }}</p>
                <div v-if="blok.startdate" class="dates"><p>📅 {{ `${newDate(blok.startdate)} ${blok.enddate === blok.startdate ? "" : blok.enddate ? " - " + newDate(blok.enddate) :  "- Ongoing"}`  }}</p></div>
            </div>
            
        </div>
        <div class="involvement" v-if="blok.pointTitle1">
            <h2>Involvement</h2>
            <div class="involvement-points">
                <ul>
                    <li><span class="list-header">{{ blok.pointTitle1 }}</span> - {{ blok.pointDescription1 }}</li>
                    <li><span class="list-header">{{ blok.pointTitle2 }}</span> - {{ blok.pointDescription2 }}</li>
                    <li><span class="list-header">{{ blok.pointTitle3 }}</span> - {{ blok.pointDescription3 }}</li>
                </ul>

            </div>

        </div>
        <div class="linkto" v-if="blok.website.url">
            <h2 class="linkto--title">View the project online</h2>
            <a target="_blank" :href="blok.website.url" class="linkto--btn">Visit site</a>
            <a target="_blank" :href="blok.website.url">
                <img class="linkto--image" :src="blok.externalPreview.filename ? blok.externalPreview.filename : blok.image?.filename || 'https://picsum.photos/300/175'" :alt="blok.image?.alt" />  
            </a>

        </div>

        <div class="linkto" v-if="blok.downloadFile.filename">
            <!-- <h2 class="linkto--title">Download now:</h2> -->
            <a target="_blank" :href="blok.downloadFile.filename" class="linkto--btn">Download PDF</a>
            <a target="_blank" :href="blok.downloadFile.filename">
                <img class="linkto--image linkto--download" :src="blok.externalPreview ? blok.externalPreview.filename : blok.image?.filename || 'https://picsum.photos/300/175'" :alt="blok.image?.alt" />  
            </a>
        </div>

        <div class="linkto" v-if="!blok.website.url && !blok.downloadFile.filename">
            <h2 class="linkto--title">Fullscreen image</h2>
            <img class="linkto--image" :src="blok.externalPreview && blok.externalPreview.filename || blok.image?.filename || 'https://picsum.photos/300/175'" :alt="blok.image?.alt" />  
        </div>
       
    </div>
    
</template>

<style scoped>

    .breadCrumbs{
        background-color: var(--black);
        color: var(--white);
        padding: 8px;
        display: flex;
        align-items: center;
        justify-content: space-evenly;
        flex-wrap: wrap;
    }

    .links{
        text-decoration:underline;
        color: var(--black);
        padding: 8px 20px;
        margin: 8px;
        background-color: var(--white);
        width: 25%;
        text-align: center;
    }
    
    .PageHeader--container{
        background-color: var(--primary );
        border-bottom: var(--highlight) solid 8px;
        color: var(--white);
        
    }
    .PageHeader--title{
        padding: 8px;
    }

    .description{
        padding: 16px 8px;
    }

    .dates{
        padding: 8px;
    }
    .intro-image {
        display: flex;
        padding: 8px;
    }
    .intro-image img{
        width: 100%;
        height: 100px;
        object-fit:cover;
        object-position: top;
        filter: opacity(50%) grayscale(80%);
    }

   

    .involvement{

	    padding: 8px;

    }
    .involvement-points ul, .involvement-points li{
        list-style: square outside;
        margin: 16px;
    }
    .linkto{
        display: flex;
        flex-direction: column;
        /* align-items: center; */

    }

    .linkto--title{
        padding: 8px;
    }

    .linkto--btn{
        display: flex;
        background-color: var(--primary);
        margin: 8px;
        padding: 16px;
        justify-content: center;
        align-items: center;
        color: var(--white);
        align-self: stretch;
        
    }
    .linkto--image{
        max-inline-size: 100%;
    }

    .linkto--download {
        /* max-width: 300px; */
        background-color: var(--primary-light);
        padding: 16px;
    }

    @media only screen and (min-width: 500px){
        .PageHeader--container, .involvement, .linkto {
            padding: 0 32px;
        }

        .involvement{
            padding-top: 32px;
        }

        .intro-image img{
            height: 300px;
            object-fit:cover;
        }

        
    }

    @media only screen and (min-width: 1024px){
        .intro-content, .involvement, .intro-image, .linkto{
            max-width: 1456px;
            margin: auto;
        }
        .breadCrumbs{
            background-color: var(--black);
            color: var(--white);
            padding: 8px;
            display: flex;
            align-items: center;
            justify-content: unset;
            flex-wrap: wrap;
    }

        .links{
            text-decoration:underline;
            color: var(--white);
            padding: unset;
            margin: 8px;
            background-color: unset;
            width: unset;
            text-align: unset;
        }
        .linkto--btn{
            align-self:flex-start;
            padding: 16px 40px;
        }
        

    }
</style>