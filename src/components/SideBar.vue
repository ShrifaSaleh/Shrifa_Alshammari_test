<template>
  <div class="sidebar">
    <div class="logo d-flex gap-2">
      <img src="@/assets/logo1.png" alt="logo" class="logo-img mb-1 ms-1" />
      <p class="text-center pt-5 ms-3">Hi TEAM</p>
    </div>
    <ul>
      <template v-for="(item, index) in menuItems" :key="index">
        <li v-if="!item.isDivider" @click="toggleSubItems(item)" :class="{ dropdown: item.subItems }">
          <a href="#" :class="{ 'active': item.active }">
            <i :class="item.icon" class="ms-2"></i> {{ item.label }}
            <i v-if="item.subItems" class="bi bi-chevron-down ms-auto"></i>
          </a>
          <ul v-if="item.showSubItems" class="child-menu">
            <li v-for="(sub, subIndex) in item.subItems" :key="subIndex">
              <a href="#" class="text-dark">
                <i class="bi bi-shield-check"></i> {{ sub }}
              </a>
            </li>
          </ul>
        </li>
        <li v-else>
          <hr style="width: 180px; margin: 5px 15px;">
        </li>
      </template>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      menuItems: [
        { label: "Dashboard", icon: "bi bi-house", active: true },
        { label: "Orders", icon: "bi bi-box" },
        { label: "Passengers", icon: "bi bi-people" },
        { label: "Captains", icon: "bi bi-bus-front-fill" },
        { label: "Categories", icon: "bi bi-card-list" },
        { isDivider: true }, 
        { label: "Settlement", icon: "bi bi-card-text" },
        { isDivider: true }, 
        { label: "Contact", icon: "bi bi-chat-left" },
        { label: "Reviews", icon: "bi bi-stars" },
        { isDivider: true }, 
        {
          label: "Permissions",
          icon: "bi bi-shield-shaded",
          subItems: ["Permissions One", "Permissions Two"],
          showSubItems: false,
        },
        { label: "Translation", icon: "bi bi-translate" },
        { label: "Education Video", icon: "bi bi-film" },
        { label: "Settings", icon: "bi bi-gear" },
        { label: "Content", icon: "bi bi-menu-up" },
      ],
    };
  },
  methods: {
    toggleSubItems(item) {
      if (item.subItems) {
        item.showSubItems = !item.showSubItems;
      }
    },
  },
};
</script>

<style scoped>
.sidebar {
  position: absolute;
  left: 0;
  top: 0;
  width: 240px; 
  height: auto;
  background-color: #FFFFFF;
  margin-left: 10px;
}

.sidebar ul {
  list-style: none;
  padding: 0px;
  margin: 1px;
}

.sidebar ul li {
  padding: 5px;
  cursor: pointer;
}

.sidebar ul li a {
  text-decoration: none;
  color: black;
  font-size: 13px;
  display: flex;
  width: 100%;
  align-items: center;
  gap: 8px;
  padding: 2px 3px;
  border-radius: 8px;
  /*transition: all 0.1s ease;*/
}

.sidebar ul li a.active {
  background-color: #575CD4;
  color: #FFFFFF;
  height: 30px;
  box-shadow: 0px 5px 20px #dedef6;
  text-shadow: 0px 0px 18px rgba(255, 255, 255, 0.6);
  font-weight: 400;
}

.sidebar ul li a:hover {
  background-color: #575CD4;
  color: white;
  height: 30px;
  box-shadow: 0px 5px 20px #dedef6;
  text-shadow: 0px 0px 25px rgba(255, 255, 255, 0.6);
}

.sidebar ul li a:hover i,
.sidebar ul li a.active i {
  color: white !important;
}

.sidebar ul li a i {
  color: rgb(145, 136, 136);
}



.child-menu li a {
  font-size: 10px;
  display: flex;
  align-items: center;
  gap: 5px;
  margin-left: 10px;
}
</style>