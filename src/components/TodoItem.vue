<template>
  <li>
    {{ getTitle }}
    <button @click="$emit('remove')">Remove</button>
  </li>
</template>

<script lang="ts">
import { computed, defineComponent } from "vue";
export default defineComponent({
  name: "TodoItem",
  components: {},
  props: {
    title: String,
  },
  setup(props) {
    const getTitle = computed(() => props.title);
    return {
      getTitle,
    };
  },
});
</script>
