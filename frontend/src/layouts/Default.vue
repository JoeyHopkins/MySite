<template>
  <v-container class="center-content">
    <div class="nav-container center-content-vertical">
      <div class="margin-horizontal-15 center-content spread">
          <router-link to="/"><div class="nav-btn center-content">Work</div></router-link>
          <router-link to="/about"><div class="nav-btn center-content">About</div></router-link>        
          <router-link to="/contact"><div class="nav-btn center-content">Contact</div></router-link>        
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