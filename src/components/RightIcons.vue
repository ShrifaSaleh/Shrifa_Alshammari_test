<template>
  <v-container class="d-flex align-center me-5" style="height: 5vh; padding: 0; gap: 10px;">
    <v-btn icon @click="toggleLanguage" style="min-width: 30px; width: 30px; height: 30px; padding: 0;">
      <v-avatar size="30">
        <img :src="selectedLanguage?.flag" :alt="selectedLanguage?.name" class="flag-img" />
      </v-avatar>
    </v-btn>
    <v-menu min-width="50px">
      <template v-slot:activator="{ props }">
        <v-btn icon v-bind="props" style="min-width: 30px; width: 30px; height: 30px;">
          <v-avatar color="gray" size="30px" style="margin-left:22px;">
            <img src="@/assets/user1.svg" alt="User Image" class="user-img " />
          </v-avatar>
          <i class="bi bi-chevron-down" style="font-size: 10px; margin-left: 8px; color: black"></i>
        </v-btn>
      </template>
      <v-card min-width="120px">
        <v-card-text>
          <div class="mx-auto text-center">
            <v-avatar size="30">
              <img src="@/assets/user1.svg" alt="User Image" class="user-img" />
            </v-avatar>
            <h6 style="font-size: 12px;">{{ user?.fullName }}</h6>
            <p class="text-caption mt-1" style="font-size: 10px;">{{ user?.email }}</p>
            <v-divider class="my-2"></v-divider>
            <v-btn variant="text" rounded style="font-size: 10px; min-height: 20px;"> Account </v-btn>
            <v-divider class="my-2"></v-divider>
            <v-btn variant="text" rounded style="font-size: 10px; min-height: 20px;"> Sign-out </v-btn>
          </div>
        </v-card-text>
      </v-card>
    </v-menu>
  </v-container>
</template>

<script>
  export default {
    data() {
      return {
        languages: [
          {
            name: "English",
            code: "en",
            flag: "https://upload.wikimedia.org/wikipedia/en/a/ae/Flag_of_the_United_Kingdom.svg",
          },
          {
            name: "العربية",
            code: "ar",
            flag: "https://upload.wikimedia.org/wikipedia/commons/0/0d/Flag_of_Saudi_Arabia.svg",
          },
            {
    name: "Français",
    code: "fr",
    flag: "https://upload.wikimedia.org/wikipedia/commons/c/c3/Flag_of_France.svg"
  },
  {
    name: "中文",
    code: "zh",
    flag: "https://upload.wikimedia.org/wikipedia/commons/f/fa/Flag_of_the_People%27s_Republic_of_China.svg"
  },
        ],
        selectedIndex: 0,
        user: {
          initials: 'MA',
          fullName: 'Mathew',
          email: 'Mathew@gmail.com',
        },
      };
    },
    computed: {
      selectedLanguage() {
        return this.languages[this.selectedIndex];
      },
    },
    methods: {
  toggleLanguage() {
    this.selectedIndex = (this.selectedIndex + 1) % this.languages.length;
    console.log(`Language changed to: ${this.selectedLanguage.name} (${this.selectedLanguage.code})`);
  },
},

  };
  </script>

<style scoped>
.flag-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 50%;
}

.user-img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  border-radius: 50%;
}
</style>