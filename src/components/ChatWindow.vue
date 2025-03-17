<template>
  <div class="chat-window">
    <div class="chat-content">
      <div v-for="(message, index) in messages" :key="index" class="chat-message" :class="{ 'user-message': message.isUser }">
        <img v-if="!message.isUser" :src="message.avatar" class="avatar" alt="User Avatar" />
        <div class="message-content">
          <span class="username">{{ message.username }}, {{ message.time }}</span>
          <div v-if="message.text" class="message-text rounded-2" :class="{ 'user-text': message.isUser }">{{ message.text }}</div>
          <img v-if="message.image" :src="message.image" class="message-image" alt="Chat Image" />
        </div>
      </div>
    </div>
    <div class="chat-input">
      <button><i class="bi bi-emoji-smile"></i></button>
      <input type="text" placeholder="Type a message" v-model="newMessage" @keyup.enter="sendMessage" />
        <button><i class="bi bi-image"></i></button>
        <button><i class="bi bi-paperclip"></i></button>
        <button><i class="bi bi-mic"></i></button>
      </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      messages: [
        { username: "Andrew", time: "2 hours ago", text: "If I don't like something, I'll stay away from it.", avatar: require('@/assets/user4.svg'), isUser: false },
        { username: "You", time: "2 hours ago", text: "If I don't like something, I'll stay away from it.", isUser: true },
        { username: "Andrew", time: "2 hours ago", text: "I want more detailed information.", avatar: require('@/assets/user4.svg'), isUser: false },
        { username: "You", time: "2 hours ago", text: "If I don't like something, I'll stay away from it.", isUser: true },
        { username: "You", time: "2 hours ago", text: "They got there early, and they got really good seats.", isUser: true },
        { username: "Andrew", time: "2 hours ago", image: require('@/assets/img1.svg'), avatar: require('@/assets/user4.svg'), isUser: false },
      ],
      newMessage: '',
    };
  },
  methods: {
    sendMessage() {
      if (this.newMessage.trim()) {
        this.messages.push({
          username: "You",
          time: "Just now",
          text: this.newMessage,
          isUser: true,
        });
        this.newMessage = '';
      }
    },
  },
};
</script>

<style scoped>
.chat-window {
  display: flex;
  flex-direction: column;
  flex: 1;
  height: 100%;
  background-color: white;
}

.chat-content {
  flex: 1;
  background: white;
  padding: 10px;
}

.chat-message {
  display: flex;
  align-items: flex-start;
  margin-bottom: 5px;
}

.user-message {
  flex-direction: row-reverse;
  text-align: right;
}

.avatar {
  width: 30px;
  height: 30px;
  border-radius: 50%;
  margin: 0 5px;
}

.message-content {
  max-width: 90%;
}

.username {
  font-size: 10px;
  color: #888;
  margin-bottom: 2px;
  display: block;
}

.message-text {
  padding: 6px;
  font-size: 10px;
  max-width: 100%;
  background-color: #EFF4FA;
}

.user-message .message-text {
  background-color: #ECFDFD;
  color: #000;
}

.message-image {
  max-width: 100px;
}

.chat-input {
  display: flex;
  align-items: center;
  border-top: 1px solid #ccc; 
  padding: 5px;
}

.chat-input input::placeholder{
  color: #98A4AE;
}

.chat-input input {
  width: 85%;
  padding: 5px;
  border: none;
  font-size: 12px;
  margin-right: 8px;
}

.chat-input i {
  display: flex;
  gap: 8px;
}

.chat-input button {
  background: none;
  border: none;
  cursor: pointer;
  font-size: 16px;
  color: #29343D;
}

.chat-input button:hover {
  color: #98A4AE; 
}
</style>
