<template>
  <div>
    <p>Received Message from Child Component: {{ message }}</p>
    <button @click="emitMessage">Emit Message</button>
  </div>
</template>

<script>
import { defineComponent, defineEmits, withDefaults } from 'vue';

const emits = withDefaults(defineEmits(), ['messageEmitted']);

export default defineComponent({
  props: {
    message: String
  },
  setup(props) {
    const emitMessage = () => {
      emits.messageEmitted('Custom message emitted from Parent Component');
    };

    return {
      emitMessage
    };
  }
});
</script>