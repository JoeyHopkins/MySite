<template>
  <v-app>
    <v-app-bar :elevation="2" color="primary">
      <v-app-bar-title color="black--text" class="title">Joey Hopkins</v-app-bar-title>
      <template v-slot:extension>
        <v-tabs
        v-model="tab"
        bg-color="transparent"
        color="basil"
        grow
      >
        <v-tab
          v-for="item in items"
          :key="item"
          :value="item"
        >
          {{ item }}
        </v-tab>
      </v-tabs>
      </template>

    </v-app-bar>
  </v-app>
</template>
<script>
  export default {
    data () {
      return {
        tab: null,
        items: [
          'About', 'Portfolio', 'Contact',
        ],
        text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
      }
    },
  }
</script>
<style scoped>
.title { 
  color: white;
  text-align: center;
}
</style>