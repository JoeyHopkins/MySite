<template>
  <v-container class="center-content" id="scroll-target">
    <div class="nav-container center-content-vertical" :class="{ 'nav-fade-in': isScrolled, 'nav-fade-out': !isScrolled }">
      <div class="margin-horizontal-15 center-content spread">
          <router-link class="nav-btn center-content" :to="{ name: 'Home' }"><div>Work</div></router-link>
          <router-link class="nav-btn center-content" :to="{ name: 'About' }"><div>About</div></router-link>        
          <router-link class="nav-btn center-content" :to="{ name: 'Contact' }"><div>Contact</div></router-link>        
      </div>
    </div>
  </v-container>
  <v-row style="padding-top: 80px">
    <v-col>
      <router-view/>
    </v-col>
  </v-row>
  <v-row style="padding-top: 80px">
    <v-col>
      <component :is="view" />
    </v-col>
  </v-row>
</template>
<script>
import Footer from '../components/Footer.vue'

export default {
  data() {
    return {
      scrollPosition: 0,
      view: Footer
    };
  },
  mounted() {
    // Add event listener for scroll
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeDestroy() {
    // Remove event listener on component destroy
    window.removeEventListener('scroll', this.handleScroll);
  },
  computed: {
    isScrolled() {
      return this.scrollPosition > 100;
    }
  },
  methods: {
    handleScroll() {
      // Update scrollPosition when user scrolls
      this.scrollPosition = window.scrollY;
    }
  }
};
</script>