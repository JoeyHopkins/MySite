<template>
  <v-app>
    <component v-bind:is="layout"></component>
  </v-app>
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