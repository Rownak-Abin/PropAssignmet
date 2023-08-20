

<template>
  <div>
    <ParentComponent :message="message" @messageEmitted="handleMessageEmitted" />
    <p>Emitted Message from ParentComponent: {{ emittedMessage }}</p>
    <input type="text" v-model="emittedMessage">
  </div>
</template>

<script>
import { defineComponent, ref } from 'vue';
import ParentComponent from './ParentComponent.vue';

export default defineComponent({
  components: {
    ParentComponent
  },
  setup() {
    const message = ref("Hello from ChildComponent");
    const emittedMessage = ref("");

    const handleMessageEmitted = (message) => {
      emittedMessage.value = message;
    };

    return {
      message,
      emittedMessage,
      handleMessageEmitted
    };
  }
});
</script>