<script setup>


const story = await useAsyncStoryblok("config", { version: "draft",
 resolve_links: 'url',
 },  )

const menu = ref(false)

function toggle() {
  menu.value = !menu.value
}

const route = useRoute()



let currentParent = ref('')

currentParent.value = route.fullPath.split('/')[1]


</script>


<template>

    <nav v-if="story && menu" class="mobile-nav">

      
      
      <h1>Menu</h1>
        <ul class="mobile-nav-navList">
          <li 
          v-if="route.path != '/'" 
          class="mobile-nav-navListItem"
          >
            <NuxtLink 
            @click="toggle" 
            class="mobile-nav-navlink" 
            to="/">
              <h2>
                🏠 Return Home
              </h2>
            </NuxtLink>
          </li>
          <li 
          v-for="blok in story.content.header_menu" 
          :key="blok._uid" 
          class="mobile-nav-navListItem"
          >
            <NuxtLink 
            @click="toggle" 
            :to="blok.link.cached_url" 
            class="mobile-nav-navlink"
            >
              <h2>{{ blok.link.story.name }}</h2>
            </NuxtLink>
          </li>
        </ul>
    </nav>
   
    <header>
      <NuxtLink to="/" class="logo"> <img
        :src="story.content.logo.filename" 
        :alt="story.content.logo.alt"
        />
      </NuxtLink>
      <button @click="toggle" class="mobile-menubtn">
        {{menu ? "Close" : ""}}
        <div class="hamburger" v-if="!menu">
          <div></div>
          <div></div>
          <div></div>
        </div>

        
      </button>

       <nav v-if="story" class="wideNav">
          <ul class="navList">
            <li 
              v-for="blok in story.content.header_menu" 
              :key="blok._uid" 
              class="navListItem"
            >
              <NuxtLink :to="'/'+blok.link.story.full_slug" class="navlink">
                <p>{{ blok.link.story.name }}</p>
              </NuxtLink>
        </li>
      </ul>
    </nav>
    </header>
      
   

</template>

<style scoped>
.logo {
  display: flex;
  align-items: center;
  justify-content: center;
}

  .wideNav{
    display:none;
  }

  h1 {
    margin-bottom: 8px;
    padding: 8px;
  }

  img{
    height: 48px;
  }

  .mobile-menubtn{
    color: var(--black);
    background-color: var(--white)
  }

  .hamburger div{

    width: 35px;
    height: 5px;
    background-color: black;
    margin: 6px 0;
    border-radius: 5px;
  }

  .mobile-nav {
    position: absolute;
    background-color: var(--primary-light);
    top: 48px;
    left: 0px;
    width: 100%;
    height: 100vh;
    margin-right: -8px;
    z-index: 1;
  }

  .mobile-nav-navList{
    padding: 8px;
    display: flex;
    flex-direction: column;
    justify-content: center;
    gap: 8px;
  }
  .mobile-nav-navListItem{
    display: flex;
    justify-content: space-around;
    flex-direction: column;
 

  }

  .mobile-nav-navlink {
    background-color: var(--primary);
    color: var(--white);
    padding: 24px 8px;
    text-decoration: none;
  }



  header {
    display: flex;
    padding: 0 8px;
    background-color: var(--white);
    justify-content: space-between;
  }

  button {
    display: flex;
    align-items: center;
    gap: 4px;
    color: #fff;
  }

  .router-link-exact-active {
      background-color: var(--highlight);
      color: var(--black);
      cursor: unset;
    }
  @media only screen and (min-width: 500px){
    header{
      padding: 0 32px;
    }
  }
  @media only screen and (min-width: 1050px){

   header{
    border-top: 20px var(--primary) solid;
    border-bottom: 20px var(--primary) solid;
   }

   .logo{
    padding-right: 128px;
   }

   .logo img {
    height: 96px;
   }
    .mobile-menubtn{
      display:none;

    }
    .wideNav{
    display:flex;
    flex: 1 1 auto;
    padding: 0 16px;
    }

    .navList{
      display: flex;
      flex: 1 1 auto;
      align-items: center;
      justify-content: space-between;
    }

    .navListItem{
      display: flex;
      
    }

    .navlink {
      text-decoration: none;
      color: var(--black)
    }

    .router-link-exact-active {
      background-color: unset;
      color: unset;
    }
    .router-link-exact-active p {
      border-bottom:4px solid var(--primary)
    }
  }


</style>