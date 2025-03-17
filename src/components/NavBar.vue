<template>
  <nav class="navbar">
    <div class="container-fluid">
      <div class="nav-left">
         <i class="bi bi-search"></i>
        <i class="bi bi-ui-radios-grid"></i>
      </div>
      <div class="nav-right">
        <i class="bi bi-moon"></i>
        <i class="bi bi-bell me-3"></i>
        <right-icons />
      </div>
    </div>
  </nav>
</template>


<script>
import RightIcons from './RightIcons.vue';

export default{
  components: {RightIcons}
}
</script>


<style scoped>
.navbar {
  position: relative;
  top: 0;
  left: 220px; 
  width: calc(100% - 220px); 
  height: 60px;
  background-color: #fff;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
}

.nav-left {
  display: flex;
  align-items: center;
}

.nav-left i {
  font-size: 20px;
  cursor: pointer;
  margin-left: 8px;
}

.nav-right {
  display: flex;
  align-items: center;
}

.nav-right i {
  margin-left: 15px;
  font-size: 20px;
  cursor: pointer;
}

</style>
