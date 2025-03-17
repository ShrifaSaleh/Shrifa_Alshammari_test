<template>
  <div class="chat-container rounded-start-4">
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
      <side-chat class="side-chat " />
      <div class="main-chat">
        <chat-header class="chat-header"  />
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
  position: relative;
  left: 12px;
  bottom: 80px;
  display: flex;
  flex-direction: column;
  align-items: left;
  width: 105%;
  height: 110vh;
  background-color: #F4F7FB;
  padding: 50px;
}

.chatnav {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 95%;
  height:50px;
  position: relative;
  /*max-width: 1200px;*/
  padding: 16px 30px;
  background-color: #ffffff;
  box-shadow: 0 2px 4px #AFB6C933;
  margin-bottom: 15px;
}

.chat-title {
  font-size: 18px;
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
  font-weight:400;
  color: #635BFF;
  height: 25px;
  background-color: #DDDBFF;
  border: none;
  padding: 0px 10px;
  cursor: pointer;
}

.chat-layout {
  display: flex;
  width: 95%;
  /* max-width: 1200px;*/
  height: 100%;
  position: relative;
  background: #ffffff;
  /*overflow: hidden;*/
  box-shadow: 0 2px 4px #AFB6C933;
  border-radius: 12px;
}

.side-chat {
  width: 44vh;
  border-right: 1px solid #ddd;
  background: white;
  overflow-y: auto;
  height: 100%;
  border-top-left-radius: 12px;
  border-bottom-left-radius: 12px;
  padding: 0px;
}

.main-chat {
  flex: 1;
  display: flex;
  flex-direction: column;
  height: 100%;
}

.chat-header {
  height: 60px;
  border-bottom: 1px solid #ddd;
  border-top-right-radius: 12px;
  background: white;
  padding: 10px;
  z-index: 2;
}

.chat-main-content {
  display: flex;
  flex-direction: row; 
  width: 96%;
  height: calc(100vh - 140px);
  gap: 0; 
}

.chat-content {
  flex: 1;
  background: white;
  overflow-y: auto;
}

.chat-media {
  width: 220px; 
  border-left: 1px solid #ddd;
  background: #f9f9f9;
}
</style>