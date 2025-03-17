<template>
    <nav-bar />
    <div class="side-bar">
      <side-bar />
      <main class="chat-details">
        <chat-details />
      </main>
    </div>
</template>

<script>
import NavBar from "./components/NavBar.vue";
import SideBar from "./components/SideBar.vue";
import ChatDetails from './components/ChatDetails.vue';

export default {
  components: {
    NavBar,
    SideBar,
    ChatDetails
  },
};
</script>

<style scoped>
.side-bar {
  display: flex;
  flex: 1;
}

.chat-details {
  flex: 1;
  padding: 20px;
  margin-left: 220px;
  margin-top: 60px;
}
</style>