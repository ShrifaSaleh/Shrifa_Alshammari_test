<template>
  <div class="chat-container rounded-4">
    <v-card class="chatnav rounded-3">
      <span class="chat-title">Chat</span>
      <div class="chat-nav-right">
        <div class="home-btn">
          <i class="bi bi-house-door text-dark"></i>
        </div>
        <span class="text-dark me-2"> / </span>
        <button class="chat-btn rounded-3">Chat</button>
      </div>
    </v-card>

    <div class="chat-layout">
      <side-chat class="side-chat" />
      <div class="main-chat">
        <chat-header class="chat-header" />
        <div class="chat-main-content">
          <div class="chat-content p-0">
            <slot>
              <chat-window />
            </slot>
          </div>
          <div class="chat-media p-0">
            <media-files />
          </div>
        </div>
      </div>
    </div>
    
  </div>
</template>

<script>
import SideChat from "@/components/SideChat.vue";
import ChatHeader from "@/components/ChatHeader.vue";
import ChatWindow from "@/components/ChatWindow.vue";
import MediaFiles from "@/components/MediaFiles.vue";

export default {
  components: {
    SideChat,
    ChatHeader,
    ChatWindow,
    MediaFiles
  },
};
</script>

<style scoped>
.chat-container {
  position: fixed;
  display: flex;
  flex-direction: column;
  align-items: left;
  width: 100%;
  height: 100vh;
  background-color: #f5f5f5;
  padding: 50px;
}

.chatnav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 80%;
  height:7vh;
  position: relative;
  bottom: 7%;
  max-width: 1200px;
  padding: 10px 20px;
  background-color: #ffffff;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
  margin-bottom: 15px;
}

.chat-title {
  font-size: 16px;
  font-weight: bold;
  color: #333;
}

.chat-nav-right {
  display: flex;
  align-items: center;
}

.home-btn {
  margin-right: 10px;
}

.chat-btn {
  font-size: 14px;
  color: #635BFF;
  background-color: #DDDBFF;
  border: none;
  padding: 5px 10px;
  cursor: pointer;
}

.chat-layout {
  display: flex;
  width: 80%;
  max-width: 1200px;
  height: 100%;
  position: relative;
  bottom: 7%;
  background: #ffffff;
  border-radius: 8px;
  overflow: hidden;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);
}

.side-chat {
  width: 240px;
  border-right: 1px solid #ddd;
  background: white;
  overflow-y: auto;
  height: 80vh;
}

.main-chat {
  flex: 1;
  display: flex;
  flex-direction: column;
  height: 100%;
}

.chat-header {
  height: 40px;
  border-bottom: 1px solid #ddd;
  background: white;
  padding: 10px;
  position: sticky;
  top: 0;
  z-index: 2;
}

.chat-main-content {
  display: flex;
  flex-direction: row; 
  height: calc(100vh - 140px);
  gap: 0; 
}

.chat-content {
  flex: 1;
  background: white;
  overflow-y: auto;
}

.chat-media {
  width: 250px; 
  border-left: 1px solid #ddd;
  background: #f9f9f9;
}
</style>