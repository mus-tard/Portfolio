<script setup>

const now = new Date;
const copyYear = now.getFullYear()

</script>
<template>
   
    <footer class="footer">
      Copyright © {{copyYear}} - Kevin Delahunt
    </footer>
      
</template>

<style scoped>

  .footer {
    background-color: var(--primary);
    padding: 16px;
    z-index: 2;
    color: var(--white);
    text-align: center;

  }


</style>