
<template>
            <div class="deets">
            <p><span class="bold">Contact</span> - 514-714-6090</p>
            <p><span class="bold">Email</span> - contact@kevd.design</p>

        </div>

  

</template>

<style scoped>
    .deets{
        padding: 8px;
    }
    .container{
        background-color: var(--primary);
        color: var(--white);
        padding: 8px;
    }

    .bold{
        font-weight: 700;
    }

    form {
        
        display:flex;
        flex-direction: column;
        

    }

    form p label {
        display:flex;
        flex-direction: column;
        padding: 16px 0;
    }

    input{
        height: 32px;
    }

    textarea{
        height: 256px;
    }

    button{
        background-color: var(--highlight);
        height: 64px;
    }

    @media only screen and (min-width: 500px){
        .container, .deets{
            padding: 32px;
        }
    }

    @media only screen and (min-width: 1024px){
        form, .deets{
        max-width: 1456px;
        margin: auto;
        }
    }
</style>