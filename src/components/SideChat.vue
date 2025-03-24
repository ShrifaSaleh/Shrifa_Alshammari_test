<template>
  <div class="sidebar">
    <div class="profile">
      <img src="@/assets/user1-2.svg" alt="User Avatar" style="width: 35px; height: 35px;" />
      <div class="user-info flex">
        <div class="name-icon">
          <h4>Mathew Anderson</h4>
          <v-menu offset-y>
            <template v-slot:activator="{ props }">
              <i class="bi bi-three-dots-vertical" v-bind="props" style="position:relative; left: 28%; cursor: pointer;"></i>
            </template>
            <v-list>
              <v-list-item v-for="(item, index) in menuItems" :key="index" @click="handleMenuItemClick(item)">
                <v-list-item-title>{{ item }}</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-menu>
        </div>
        <p>Marketing Director</p>
      </div>
    </div>

    <div class="search-container rounded">
      <i class="bi bi-search"></i>
      <input type="text" v-model="searchQuery" placeholder="Search contacts" class="search-box" />
    </div>

    <div class="d-flex align-items-center recent-header mt-5">
      <p @click="toggleSortMenu" class="text-sm recent-label mb-5" style="cursor: pointer;">Recent Chats</p>
      <v-menu v-model="showSortMenu" offset-y>
        <template v-slot:activator="{ props }">
          <i class="bi bi-chevron-down ms-1 mb-2" v-bind="props" style="cursor: pointer; font-size:8px; color:#98A4AE;"></i>
        </template>
        <v-list>
          <v-list-item @click="sortBy('date')">
            <v-list-item-title>Sort by Date</v-list-item-title>
          </v-list-item>
          <v-list-item @click="sortBy('name')">
            <v-list-item-title>Sort by Name</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </div>

 <div v-for="contact in filteredContacts" :key="contact.id" class="contact" :class="{ 'active-contact': contact.name === 'Michell Flintoff' }">
     
  
      <img :src="contact.avatar" alt="Avatar" class="contact-img" />
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
      searchQuery: "",
      contacts: [
        { id: 1, name: 'Michell Flintoff', lastMessage: 'Yesterday was great...', avatar: require('@/assets/user2.svg'), time: '15 minutes', timestamp: 1678255100 },
        { id: 2, name: 'Bianca Anderson', lastMessage: 'Nice looking dress you...', avatar: require('@/assets/user3.svg'), time: '30 minutes', timestamp: 1678254800 },
        { id: 3, name: 'Andrew Johnson', lastMessage: 'Sent a photo', avatar: require('@/assets/user4.svg'), time: '2 hours', timestamp: 1678254400 },
        { id: 4, name: 'Mark Strokes', lastMessage: 'Lorem ipsum text sud...', avatar: require('@/assets/user5.svg'), time: '5 days', timestamp: 1678240000 },
        { id: 5, name: 'Mark, Stoinus & Rish...', lastMessage: 'Lorem ipsum text ...', avatar: require('@/assets/user6.svg'), time: '5 days', timestamp: 1678240000 },
        { id: 6, name: 'Bianca Anderson', lastMessage: 'Nice looking dress you...', avatar: require('@/assets/user7.svg'), time: '30 minutes', timestamp: 1678254800 }
      ],
      menuItems: ['Show Profile', 'Setting'],
      showSortMenu: false
    };
  },
  computed: {
    filteredContacts() {
      return this.contacts.filter(contact => 
        contact.name.toLowerCase().includes(this.searchQuery.toLowerCase())
      );
    }
  },
  methods: {
    sortBy(type) {
      if (type === 'date') {
        this.contacts.sort((a, b) => b.timestamp - a.timestamp);
      } else if (type === 'name') {
        this.contacts.sort((a, b) => a.name.localeCompare(b.name));
      }
    },
    handleMenuItemClick(item) {
      alert(`You clicked on ${item}`);
    },
    toggleSortMenu() {
      this.showSortMenu = !this.showSortMenu;
    }
  }
};
</script>

<style scoped>
.sidebar {
  background: white;
  border-right: 1px solid #949798;
}

.profile {
  display: flex;
  align-items: center;
  gap: 10px; 
  margin: 20px;
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
  border: 1px solid #E0E6EB;
  background: white;
  margin: 20px;
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

.search-box::placeholder {
  color: #29343D;
}

.recent-label {
  color: #98A4AE;
  font-size: 10px;
  margin-top: 10px;
  padding-left: 20px;
}

.contact {
  display: flex;
  align-items: center;
  position: relative;
  padding-left: 20px;
}

.contact:hover {
  background-color: #F6F7F9;
  height: auto;
}

.active-contact {
  background-color: #F6F7F9;
}


.contact-img {
  width: 30px; 
  height: 30px;
  margin-right: 8px;
  margin-bottom: 10px;
  margin-top: 5px;
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
  margin-top: 10px;
}

.contact-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
}

.contact-header h4 {
  font-size: 11px;
  margin: 0px;
}

.msg-time {
  font-size: 8px;
  color: #98A4AE;
  position: absolute;
  right: 0px;
  bottom: 15px;
  padding-right: 20px;
}

.last-message {
  font-size: 9px;
  color: #98A4AE;
  margin-top: 2px;
}
</style>
