<template>
  <v-container class="center-content">
    <div class="nav-container center-content-vertical">
      <div class="margin-horizontal-15 center-content spread">
        <div class="nav-btn center-content">
          Work
        </div>
        <div class="nav-btn center-content">
          About
        </div>
        <div class="nav-btn center-content">
          Contact
        </div>
      </div>
    </div>
  </v-container>
  <v-row>
    <v-col>
      <router-view/>
    </v-col>
  </v-row>
</template>
<script>
export default {
  data() {
    return {
    }
  },
  methods: {
  },
  mounted() {
  }
}
</script>