<template>
  <div class="title q-pa-md text-primary text-bold">{{ title }}</div>
</template>

<script>
import { defineComponent } from 'vue';

export default defineComponent({
  name: 'TitleFormsComponent',

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
  font-size: 30px;
}
</style>
