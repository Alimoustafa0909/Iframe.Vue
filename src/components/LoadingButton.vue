<template>
  <Button
    :label="loading ? 'Loading...' : label"
    :icon="loading ? 'pi pi-spin pi-spinner' : icon"
    :disabled="loading"
    @click="handleClick"
    :class="customClass"
  />
</template>

<script>
import { ref } from 'vue';
import Button from 'primevue/button';

export default {
  name: 'LoadingButton',
  components: {
    Button,
  },
  props: {
    label: {
      type: String,
      default: 'Click Me',
    },
    icon: {
      type: String,
      default: '',
    },
    customClass: {
      type: String,
      default: ''
    }
  },
  setup(props, { emit }) {
    const loading = ref(false);

    const handleClick = () => {
      loading.value = true;
      emit('click', () => {
        setTimeout(() => {
          loading.value = false;
        }, 3000); // Change this timeout as needed
      });
    };
    

    return {
      loading,
      handleClick,
    };
  },
};
</script>

<style scoped>
.pi-spin {
  animation: pi-spin 1s infinite linear;
}
@keyframes pi-spin {
  100% {
    transform: rotate(360deg);
  }
}
</style>
