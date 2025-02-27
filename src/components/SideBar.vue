<template>
  <div class="sidebar">
    <div class="logo d-flex gap-2 py-3">
      <img src="@/assets/logo1.png" alt="logo" class="logo-img" />
      <p class="text-center pt-3 ms-3">Hi TEAM</p>
    </div>
    <ul>
      <template v-for="(item, index) in menuItems" :key="index">
        <li v-if="!item.isDivider" @click="item.toggle ? item.toggle() : null" :class="{ dropdown: item.subItems }">
          <a href="#" :class="{ 'active': item.active }">
            <i :class="item.icon" class="ms-2"></i> {{ item.label }}
            <i v-if="item.subItems" class="bi bi-chevron-down ms-auto"></i>
          </a>
          <ul v-if="item.label === 'Permissions'" v-show="showPermissions" class="dropdown-menu">
            <li v-for="(sub, subIndex) in item.subItems" :key="subIndex">
              <a href="#" class="text-dark">{{ sub }}</a>
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
      showPermissions: false,
      menuItems: [
        { label: "Dashboard", icon: "bi bi-house", active: true },
        { label: "Orders", icon: "bi bi-cart" },
        { label: "Passengers", icon: "bi bi-people" },
        { label: "Captains", icon: "bi bi-bus-front-fill" },
        { label: "Categories", icon: "bi bi-card-list" },
        { isDivider: true }, 
        { label: "Settlement", icon: "bi bi-journal-text" },
        { isDivider: true }, 
        { label: "Contact", icon: "bi bi-chat" },
        { label: "Reviews", icon: "bi bi-stars" },
        { isDivider: true }, 
        {
          label: "Permissions",
          icon: "bi bi-shield-check",
          subItems: [" permissions one", "Permissions two"],
          toggle: () => (this.showPermissions = !this.showPermissions),
        },
        { label: "Translation", icon: "bi bi-translate" },
        { label: "Education Video", icon: "bi bi-film" },
        { label: "Settings", icon: "bi bi-gear" },
        { label: "Content", icon: "bi bi-menu-up" },
      ],
    };
  },
};
</script>

<style scoped>
.sidebar {
  position: fixed;
  left: 0;
  top: 0;
  width: 220px;
  height: 100vh;
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
  font-size: 12px;
  display: flex;
  width: 100%;
  align-items: center;
  gap: 8px;
  padding: 2px 0px;
  border-radius: 8px;
  transition: all 0.3s ease;
}

.sidebar ul li a.active {
  background-color: #575CD4;
  color: white;
  height: 30px;
}

.sidebar ul li a:hover {
  background-color: #575CD4;
  color: white;
  height: 30px;
}

.sidebar ul li a:hover i,
.sidebar ul li a.active i {
  color: white !important;
}

.sidebar ul li a i {
  color: rgb(145, 136, 136);
}

.dropdown-menu {
  display: none;
  padding-left: 20px;
}

.dropdown-menu li {
  padding: 8px 0;
}

.dropdown:hover .dropdown-menu {
  display: block;
}

.logo {
  display: flex;
  align-items: center;
  gap: 10px;
  padding: 5px;
}

.logo-img {
  width: 50px;
  height: auto;
}
</style>
