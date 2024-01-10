<template>
  <v-container class="center-content">
    <div class="nav-container center-content-vertical">
      <div class="margin-horizontal-15 center-content spread">
          <router-link class="nav-btn center-content" :to="{ name: 'Home' }"><div>Work</div></router-link>
          <router-link class="nav-btn center-content" :to="{ name: 'About' }"><div>About</div></router-link>        
          <router-link class="nav-btn center-content" :to="{ name: 'Contact' }"><div>Contact</div></router-link>        
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