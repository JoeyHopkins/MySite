<template>
  <v-container class="center-content" id="scroll-target">
    <div class="nav-container center-content-vertical"
      :class="{ 'nav-fade-in': isScrolled, 'nav-fade-out': !isScrolled }">
      <div class="margin-horizontal-15 center-content spread">
        <router-link class="nav-btn center-content" :to="{ name: 'Home' }">
          <div>Work</div>
        </router-link>
        <router-link class="nav-btn center-content" :to="{ name: 'About' }">
          <div>About</div>
        </router-link>
        <button class="nav-btn center-content" @click="toggleChat">Contact</button>
      </div>
    </div>
  </v-container>
  <v-row class="main-page-containter">
    <v-col>
      <router-view />
    </v-col>
  </v-row>
  <Chatbot :isOpen="showChatbot" @toggle-chat="toggleChat" />
  <component :is="view" />
</template>
<script>
import Footer from '../components/Footer.vue'
import Chatbot from '../components/Chatbot.vue';

export default {
  components: {
    Chatbot,
  },
  data() {
    return {
      scrollPosition: 0,
      view: Footer,
      showChatbot: false
    };
  },
  mounted() {
    window.addEventListener('scroll', this.handleScroll);
  },
  beforeDestroy() {
    window.removeEventListener('scroll', this.handleScroll);
  },
  computed: {
    isScrolled() {
      return this.scrollPosition > 100;
    }
  },
  methods: {
    handleScroll() {
      this.scrollPosition = window.scrollY;
    },
    toggleChat() {
      this.showChatbot = !this.showChatbot;
      console.log(this.showChatbot)
    }
  }
};
</script>