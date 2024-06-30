<template>
  <v-app>
    <v-container fluid class="p-4 fill-height container-bg">
      <!-- Header -->
      <v-app-bar app flat color="transparent">
        <v-btn icon="mdi-arrow-left" @click="goBack" density="compact"></v-btn>
        <v-toolbar-title class="ml-2">Messages</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-avatar size="40" class="elevation-2">
          <v-img src="https://cdn.vuetifyjs.com/images/john.jpg"></v-img>
        </v-avatar>
      </v-app-bar>

      <!-- Main Content -->
      <v-row no-gutters class="fill-height pt-16">
        <!-- Sidebar -->
        <v-col cols="12" sm="4" md="3" lg="2" style="height: 100%">
          <v-card class="ma-2" color="white" style="height: 100%">
            <v-card-title class="d-flex justify-space-between align-center bg-soild-[#e8eaf9] text-[#e8eaf9]">
              DM Settings
              <v-btn icon="mdi-close" density="compact" color="transparent" flat></v-btn>
            </v-card-title>
            <v-list>
              <v-list-item v-for="(item, index) in listItems" :key="index" :value="index">
                <template v-slot:prepend>
                  <v-icon :icon="item.icon" class="mr-3"></v-icon>
                </template>
                <v-list-item-title>{{ item.title }}</v-list-item-title>
              </v-list-item>
            </v-list>
            <v-subheader class="text-grey">Other Items</v-subheader>
            <v-list>
              <v-list-item v-for="(item, index) in otherItems" :key="index">
                <template v-slot:prepend>
                  <v-icon :icon="item.icon" class="mr-3"></v-icon>
                </template>
                <v-list-item-title>{{ item.title }}</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-card>
        </v-col>

        <!-- Body -->
        <v-col cols="12" sm="8" md="9" lg="10">
          <v-card class="ma-2 fill-height" color="white" style="opacity: 0.5;">
            <v-card-text>This is the body of the component.</v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<script setup>
import { ref } from "vue";

const selectedItem = ref(0);
const listItems = [
  { title: "DM tour guide", icon: "mdi-map-marker" },
  { title: "Item 1", icon: "mdi-account" },
  { title: "Item 2", icon: "mdi-heart" },
  { title: "Item 3", icon: "mdi-star" },
];
const otherItems = [
  { title: "Other item 1", icon: "mdi-folder" },
  { title: "Other item 2", icon: "mdi-cog" },
];

const goBack = () => {
  // Implement your back navigation logic here
  console.log("Going back");
};
</script>

<style scoped>
.container-bg {
  background-color: #e8eaf9;
}
</style>