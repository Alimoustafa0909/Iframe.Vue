<template>
  <div id="app">
    <Button
      id="btnSendMessage"
      @click="startShare"
      :label="loading ? 'Loading...' : 'Share'"
      :icon="loading ? 'pi pi-spin pi-spinner' : 'pi pi-share'"
      :disabled="loading"
    />
    <Button id="btnFetchName" @click="fetchName" label="Fetch Name" icon="pi pi-search" />
  </div>
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";
import Button from "primevue/button";

const loading = ref(false);

const startShare = () => {
  loading.value = true;
  console.log("Start sharing process");
  window.parent.postMessage({ action: "Sharee" }, "*");
};

const fetchName = () => {
  console.log("Fetching name from document");
  window.parent.postMessage({ action: "fetchName" }, "*");
};

window.addEventListener("message", event => {
  if (event.data.action === "fetchComplete") {
    loading.value = false;
    console.log("Fetch complete, stop loading");
  } else if (event.data.action === "sendName") {
    console.log("Received name:", event.data.name);
    // Handle the received name here, e.g., display it in the UI
  }
});
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.pi-spin {
  animation: pi-spin 1s infinite linear;
}

@keyframes pi-spin {
  100% {
    transform: rotate(360deg);
  }
}
</style>
