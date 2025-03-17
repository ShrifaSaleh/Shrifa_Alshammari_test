<template>
  <div class="chat-header">
    <div class="profile">
      <div class="avatar-wrapper">
        <img src="@/assets/user2.svg" alt="User Avatar" class="avatar" />
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
    <v-dialog v-model="dialog" max-width="492" style="height:323; border-radius:10px;">
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
          this.dialogMessage = "Once You Sure To Delete This Conversation , You Will Not Be Able To Undo This Action";
          this.dialogIcon = "bi bi-trash trash-icon";
          break;
        case "menu":
          this.dialogTitle = "Unlock User";
          this.dialogMessage = "You Are Going To Unblock This User , Are You Sure?";
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
}

.profile {
  display: flex;
  align-items: center;
  gap: 10px;
}

.avatar {
  width: 35px;
  height: 35px;
}

.status {
  color: gray;
  font-size: 14px;
}

.icons {
  display: flex;
  gap: 22px;
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
  font-weight: 400px;
}
.text{
  color: #717171;
  font-size: 14px;
  text-align: center;
}

.Yes{
  color: white;
  background-color: #575CD4;
  margin-bottom: 15px;
  margin-left: 25px;
  text-transform: capitalize;
  width: 110px;
  font-size: 14px;
  font-weight: 400;
}


.Cancel{
  color: white;
  background-color:#959595;
  margin-bottom: 15px;
  margin-right: 25px;
  text-transform:capitalize;
  width: 110px;
   font-size: 14px;
  font-weight: 400;
}

.dialogIcon i {
  font-size: 30px;
  color: #575CD4;
}

</style>
