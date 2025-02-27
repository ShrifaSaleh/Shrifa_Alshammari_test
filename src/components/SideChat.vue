 <template>
 <div class="sidebar">
    <div class="profile">
      <img src="@/assets/user1.svg" alt="User Avatar" style="width: 30px; height: 30px;" />
      <v-badge dot color="green" class="status-badge m-4 mb-3"></v-badge>
      <div class="user-info flex">
        <div class="name-icon">
          <h4>Mathew Anderson</h4>
          <i class="bi bi-three-dots-vertical" style="margin-left:25px;"></i>
          </div>
          <p>Marketing Director</p>
        </div>
      </div>
          
      <div class="search-container rounded-1">
        <i class="bi bi-search"></i>
        <input type="text" placeholder="Search contacts" class="search-box" />
      </div> 
      <div class="d-flex align-items-center recent-header">
        <p class="text-sm recent-label mt-1 mb-4">Recent Chats</p>
        <i class="bi bi-chevron-down ms-1 mb-2" style="font-size: 5px; color:#98A4AE" ></i>
      </div>
      
      <div v-for="contact in contacts" :key="contact.id" class="contact p-0">
        <img :src="contact.avatar" alt="Avatar" class="contact-img" />
        <v-badge :color="getStatusColor(contact.status)" dot class="status-badge m-4" ></v-badge>
        
        <div class="contact-info">
          <div class="contact-header">
            <h4>{{ contact.name }}</h4>
            <p class="msg-time">{{ contact.time }}</p>
          </div>
          <p class="last-message">{{ contact.lastMessage }}</p>
        </div>
      </div>
  </div>
</template>

<script>
export default {
  data() {
  return {
    contacts: [
      { id: 1, name: 'Michell Flintoff', lastMessage: 'Yesterday was great...', avatar: require('@/assets/user2.svg'), time: '15 minutes', status: 'online'},
      { id: 2, name: 'Bianca Anderson', lastMessage: 'Nice looking dress you...', avatar: require('@/assets/user3.svg'), time: '30 minutes', status: 'busy' },
      { id: 3, name: 'Andrew Johnson', lastMessage: 'Sent a photo', avatar: require('@/assets/user4.svg'), time: '2 hours', status: 'away' },
      { id: 4, name: 'Mark Strokes', lastMessage: 'Lorem ipsum text sud...', avatar: require('@/assets/user5.svg'), time: '5 days', status: 'online' },
      { id: 5, name: 'Mark, Stoinus & Rish...', lastMessage: 'Lorem ipsum text ...', avatar: require('@/assets/user6.svg'), time: '5 days', status: 'online' },
      { id: 6, name: 'Bianca Anderson', lastMessage: 'Nice looking dress you...', avatar: require('@/assets/user7.svg'), time: '30 minutes', status: 'busy' }        
    ]
  };
},
methods: {
  getStatusColor(status) {
    switch (status) {
      case 'online': return 'success'; 
      case 'away': return 'yellow';  
      case 'busy': return 'pink';      
      default: return 'grey';        
    }}}}
</script>

<style scoped>
.sidebar {
  height: 80vh;
  background: white;
  padding: 20px;
  border-right: 1px solid #949798;
}

.profile {
  display: flex;
  align-items: center;
  gap: 10px; 
}

.profile img {
  width: 30px; 
  height: 30px;
  border-radius: 50%;
}

.profile p {
  font-size: 8px;
  color: #98A4AE;
  margin: 2px 0 0 0;
}

.user-info {
  display: flex;
  flex-direction: column;
}

.name-icon {
  display: flex;
  align-items: center;
  gap: 5px; 
}

.name-icon i {
  font-size: 14px;
  cursor: pointer;
  margin-left: 15px;
}

.profile h4 {
  font-size: 13px;
  margin-bottom: 0px;
}

.search-container {
  height: 25px;
  position: relative;
  display: flex;
  align-items: center;
  margin-top: 10px;
  margin-bottom: 30px;
  border: 1px solid #ddd;
  padding: 0px;
  background: white;
}

.search-container i {
  position: absolute;
  left: 12px;
  color: #29343D;
  font-size: 14px;
}

.search-box {
  width: 90%;
  height: 60px;
  padding: 10px 10px 10px 35px; 
  border: none;
  outline: none;
  font-size: 12px;
  background: transparent;
}

.recent-label {
  color: #98A4AE;
  font-size: 10px;
  margin-top: 10px;
}

.contact {
  display: flex;
  align-items: center;
  position: relative;
}

.contact:hover{
  background-color: #F6F7F9;
  border-radius: 6px; 
}

.contact-img {
  width: 27px; 
  height: 27px;
  border-radius: 50%;
  margin-right: 8px;
  margin-bottom: 15px;
  position: relative;
}

.status-badge {
  position: absolute;
  border: 2px solid white; 
  width: 8px;
  height: 8px;
  border-radius: 50%;
}

.contact-info {
  display: flex;
  flex-direction: column;
  flex-grow: 1;
}

.contact-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
}

.contact-header h4 {
  font-size: 11px;
  margin: 0;
}

.msg-time {
  font-size: 8px;
  color: #98A4AE;
  position: absolute;
  right: 0px;
  bottom: 15px;
}

.last-message {
  font-size: 9px;
  color: #98A4AE;
  margin-top: 2px;
}
</style> 