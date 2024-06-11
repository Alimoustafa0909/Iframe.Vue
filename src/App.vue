<template>
<Button id="btnSendMessage"  @click="handleTestButton"  label="share" severity="share" />
  
</template>

  

<script setup  lang="ts">
import Button from 'primevue/button';


const handleTestButton = () => {
  console.log('tesstt ')

      window.parent.postMessage("Sharee", "*" )
     
  }
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
