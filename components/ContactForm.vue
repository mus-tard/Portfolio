<script setup>

const handleSubmit = (event) => {

  const myForm = event.target;
  const formData = new FormData(myForm);
  
  fetch("/", {
    method: "POST",
    headers: { "Content-Type": "application/x-www-form-urlencoded" },
    body: new URLSearchParams(formData).toString(),
  })
    .then(() => console.log("Form successfully submitted"))
    .catch((error) => alert(error));
};


</script>

<template>
            <div class="deets">
            <p><span class="bold">Contact</span> - 514-714-6090</p>
            <p><span class="bold">Email</span> - contact@kevd.design</p>

        </div>
    <div class="container">

        <form name="contact" @submit.prevent="handleSubmit" data-netlify="true">
            <p>
                <label>Your Name: <input type="text" name="name" /></label>
            </p>
            <p>
                <label>Your Email: <input type="email" name="email" /></label>
            </p>
            <p>
                <label>Message: <textarea name="message"></textarea></label>
            </p>
            <button type="submit">Send</button>

        </form>
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