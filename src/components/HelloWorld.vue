<template>
  <div class="button-container">
    <LoadingButton
      label="Submit"
      icon="pi pi-check"
      @click="handleButtonClick"
      customClass="button"
    />
    <LoadingButton
      label="Delay"
      icon="pi pi-clock"
      @click="handleDelayButtonClick"
      customClass="button"
    />
  </div>
</template>

<script>
import { defineComponent } from 'vue';
import Button from 'primevue/button';
import LoadingButton from './LoadingButton.vue'; // Adjust the path as necessary

export default defineComponent({
  components: {
     LoadingButton,
  }, 
    setup() {
    const handleButtonClick = (done) => {
      // Simulate an async operation (e.g., an API call)
      setTimeout(() => {
        console.log('Button clicked!');
        done(); // Call this function to stop the loading state
      }, 3000);
    };
      const handleDelayButtonClick = (done) => {
      // Simulate a delay of 3 seconds after performing its function
      console.log('Delay button clicked!');
      setTimeout(() => {
        console.log('Delay button function completed after 3 seconds');
        done(); // Call this function to stop the loading state
      }, 3000);
    };

    return {
      handleButtonClick,
      handleDelayButtonClick,
    };
  },
});

</script>

<style>
@import 'primevue/resources/themes/saga-blue/theme.css';
@import 'primevue/resources/primevue.min.css';
@import 'primeicons/primeicons.css';
@import 'primeflex/primeflex.css';

.button-container {
  display: flex;
  flex-direction: column;
  padding: 10px;
  
  width: fit-content;
  margin: 20px;
}
.button {
  margin-top: 30px; /* Add spacing between buttons */
}
</style>
