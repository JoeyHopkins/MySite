<template>
  <v-card class="chatbot" :class="{ 'open': isOpen }">
    <div class="chat-header">
      <v-row class="spread mx-5 py-5">
        <h3 class="text-white">Joeys Chatbot</h3>
        <span class="close-btn" @click="toggleChat">X</span>
      </v-row>
    </div>
    <div class="chat-body border">
      <div ref="messagesContainer" class="messages-container">
        <div v-for="(message, index) in messages" :key="index" :class="{ 'set-end': message.class === 'user-message' }">
          <div class="message" :class="message.class">
            {{ message.text }}
          </div>
        </div>
        <div v-for="(message, index) in userResponseMessages" :key="index" class="set-end">
          <div v-if="message.id != 0">
            <div @click="selectedResponse(message)" class="message" :class="message.class">
              {{ message.text }}
            </div>
          </div>
        </div>
        <div ref="scrollTo"></div>
      </div>
    </div>
  </v-card>
</template>  
<script>
export default {
  props: {
    isOpen: {
      type: Boolean,
      required: true
    }
  },
  data() {
    return {
      messages: [],
      initialMessages: [
        { text: 'Hi there!', class: 'bot-message' },
        { text: 'How can I help you today??', class: 'bot-message' },
      ],
      userResponseMessages: [],
      userInitialResponseMessages: [
        { id: 1, text: "Let's work Together!!", class: 'user-response-message' },
        { id: 2, text: "We would like to hire you!!", class: 'user-response-message' },
      ],
      email: "Joseph.Hopkins1095@gmail.com"
    };
  },
  methods: {
    toggleChat() {
      this.$emit('toggle-chat');
    },
    selectResponse(userMessage) {
      this.messages.push({ text: userMessage.text, class: 'user-message' });
      this.scrollMessagesToBottom();
    },
    scrollMessagesToBottom() {
      const container = this.$refs.messagesContainer;
      container.scrollTop = container.scrollHeight;
    },
    async selectedResponse(message) {
      console.log(message)
      this.userResponseMessages = []
      this.addMessage({ text: message.text, class: 'user-message' })

      switch (message.id) {
        case -1:
          await this.sleep(1000)
          this.addMessage({ text: "Sure!", class: 'bot-message' })
          await this.sleep(1000)
          this.addMessage({ text: "How can I help you today??", class: 'bot-message' })
          await this.sleep(1000)
          for (let message of this.userInitialResponseMessages)
            this.addUserResponseMessage(message)
          break
        case 1:
          await this.sleep(1000)
          this.addMessage({ text: "Awesome!", class: 'bot-message' })
          await this.sleep(1000)
          this.addMessage({ text: "Send me a message and let's talk!", class: 'bot-message' })
          await this.sleep(1000)
          this.addMessage({ text: "Send me an email at " + this.email, class: 'bot-message' })
          await this.sleep(1000)
          this.addUserResponseMessage({ id: -1, text: "Let's start over", class: 'user-response-message' })
          break
        case 2:
          await this.sleep(1000)
          this.addMessage({ text: "I appriciate the opportunity!", class: 'bot-message' })
          await this.sleep(1000)
          this.addMessage({ text: "Send the job details and additional information to " + this.email, class: 'bot-message' })
          await this.sleep(1000)
          this.addUserResponseMessage({ id: -1, text: "Let's start over", class: 'user-response-message' })
          break

      }
    },
    addMessage(message) {
      this.messages.push(message);
      this.$nextTick(() => {
        setTimeout(() => {
          this.scrollMessagesToBottom();
        }, 100);
      });
    },
    addUserResponseMessage(message) {
      this.userResponseMessages.push(message);
      this.$nextTick(() => {
        setTimeout(() => {
          this.scrollMessagesToBottom();
        }, 100);
      });
    },
    sleep(ms) {
      return new Promise(resolve => setTimeout(resolve, ms));
    }
  },
  mounted() {
    for (let message of this.initialMessages)
      this.messages.push(message)

    for (let message of this.userInitialResponseMessages)
      this.userResponseMessages.push(message)
  },
};
</script>
  
<style scoped>
.chatbot {
  position: fixed;
  bottom: 80px;
  right: 20px;
  width: 400px;
  border: 1px solid #ccc;
  border-radius: 10px;
  background-color: #fff;
  transition: transform 0.3s ease-out;
  transform: translateY(100%);
  opacity: 0;
  pointer-events: none;
}

.chatbot.open {
  transform: translateY(0);
  opacity: 1;
  pointer-events: auto;
}

.chat-header {
  background-color: darkorchid;
  padding: 10px;
  border-bottom: 1px solid #ccc;
}

.close-btn {
  cursor: pointer;
  margin-top: 2px;
  color: white;
}

.chat-body {
  max-height: 400px;
  overflow-y: auto;
  overflow-x: hidden;
}

.messages-container {
  overflow-y: auto;
  max-height: 300px;
}

.bot-message {
  background-color: #52afee;
  border-radius: 20px;
  width: fit-content;
  max-width: 65%;
}

.user-message {
  background-color: #55da98;
  border-radius: 20px;
  max-width: 60%;
}

.user-response-message {
  border: 2px solid #55da98;
  border-radius: 20px;
  width: auto;
  transition: background-color 0.3s;
  cursor: pointer;
}

.message {
  margin: 10px;
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 10px;
  opacity: 0;
  animation: fadeInUp .5s ease forwards;
}

@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }

  to {
    opacity: 1;
    transform: translateY(0);
  }
}
</style>