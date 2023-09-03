<template>
  <div class="title">{{ title }}</div>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'SubtitleFormsComponent',

  props: {
    title: {
      type: String,
      required: true,
    },
  },
});
</script>

<style scoped>
.title {
  font-size: 20px;
}
</style>
