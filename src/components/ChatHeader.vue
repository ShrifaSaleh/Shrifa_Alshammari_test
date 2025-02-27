<template>
  <div class="chat-header">
    <div class="profile">
      <div class="avatar-wrapper">
        <img src="@/assets/user2.svg" alt="User Avatar" class="avatar" />
        <v-badge dot color="green" class="status-badge"></v-badge>
      </div>
      <span class="status">Away</span>
    </div>
    <div class="icons">
      <i class="bi bi-ban ban-icon" @click="openDialog('ban')"></i>
      <i class="bi bi-trash trash-icon" @click="openDialog('delete')"></i>
      <i class="bi bi-telephone phone-icon"></i>
      <i class="bi bi-camera-video video-icon"></i>
      <i class="bi bi-list menu-icon" @click="openDialog('menu')"></i>
    </div>
    <v-dialog v-model="dialog" max-width="400">
      <v-card class="d-flex flex-column align-center">
        <div class="dialogIcon">
          <i :class="dialogIcon"></i>
        </div>
        <v-card-title class="title">{{ dialogTitle }}</v-card-title>
        <v-card-text class="text">{{ dialogMessage }}</v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn class="Cancel" @click="dialog = false">Cancel</v-btn>
          <v-btn class="Yes" @click="confirmAction">Yes</v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dialog: false,
      dialogTitle: "",
      dialogMessage: "",
      dialogIcon: "",
      currentAction: "",
    };
  },
  methods: {
    openDialog(action) {
      this.currentAction = action;
      switch (action) {
        case "ban":
          this.dialogTitle = "Block User";
          this.dialogMessage = "You Are Going To Block This User,Are you sure?";
          this.dialogIcon = "bi bi-ban";
          break;
        case "delete":
          this.dialogTitle = "Delete Conversation";
          this.dialogMessage = "once you sure to delete this conversation , you will not be able to undo this action";
          this.dialogIcon = "bi bi-trash trash-icon";
          break;
        case "menu":
          this.dialogTitle = "Unlock User";
          this.dialogMessage = "you are going to unblock this user , are you sure?";
          this.dialogIcon = "bi bi-unlock"
          break;
      }
      this.dialog = true;
    },
    confirmAction() {
      this.dialog = false;
      switch (this.currentAction) {
        case "ban":
          console.log("User blocked!");
          break;
        case "delete":
          console.log("Chat deleted!");
          break;
        case "menu":
          console.log("User unlocked!");
          break;
      }
    },
  },
};
</script>

<style scoped>
.chat-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 10px;
  background: white;
  border-bottom: 1px solid #949798;;
}

.profile {
  display: flex;
  align-items: center;
  gap: 10px;
}

.avatar {
  width: 30px;
  height: 30px;
  border-radius: 50%;
}

.status {
  color: gray;
  font-size: 14px;
}

.icons {
  display: flex;
  gap: 15px;
}

.icons i {
  font-size: 18px;
  cursor: pointer;
  transition: 0.3s ease;
}


.ban-icon {
  color: #6c63ff;
}
.trash-icon {
  color: red;
}
.phone-icon {
  color: black;
}
.video-icon, .menu-icon {
  color: black;
}

.icons i:hover {
  opacity: 0.7;
}

.title{
  color: black;
  font-size: 25px;
}
.text{
  color: gray;
  font-size: 14px;
  text-align: center;
}

.Yes{
  color: white;
  background-color: #575CD4;
  margin-bottom: 15px;
  margin-left: 10px;
}


.Cancel{
  color: white;
  background-color:gray;
  margin-bottom: 15px;
  margin-right: 10px;
  
}

.dialogIcon i {
  font-size: 50px;
  color: #575CD4;
}

</style>
