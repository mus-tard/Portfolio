<script setup>

const now = new Date;
const copyYear = now.getFullYear()

</script>
<template>
   
    <footer class="footer">
      <div class="deets">
        <p>514-714-6090</p>
        <p>contact@kevd.design</p>
      </div>

      <div>Copyright © {{copyYear}} - Kevin Delahunt</div>
    </footer>
      
</template>

<style scoped>

  .footer {

    display: flex;
    flex-direction: column;
    justify-content: space-between;
    align-items: center;
    background-color: var(--black);
    padding: 8px;
    color: var(--white);



  }

  .deets{
    padding: 8px;
    display: flex;
    flex-direction: column;
    text-align: center;
    gap: 8px;
    /* align-items: baseline; */
  }
  @media only screen and (min-width: 500px){
    .deets{
      flex-direction: row;
      gap: 32px;
    }
  }

</style>