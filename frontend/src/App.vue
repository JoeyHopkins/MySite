<template>
  <component v-bind:is="layout"></component>
</template>
<script>
import LayoutDefault from "@/layouts/Default.vue";
export default {
  data() {
    return {};
  },
  computed: {
    layout() {
      return LayoutDefault;
    },
  },
};
</script>
<style scoped></style>