<template>
  <v-app theme="dark">
    <v-container fluid class="pa-0 fill-height bg-grey-darken-4">
      <!-- Header -->
      <v-app-bar app flat color="transparent">
        <v-btn icon @click="goBack">
          <v-icon>mdi-arrow-left</v-icon>
        </v-btn>
        <v-toolbar-title class="ml-2">Messages</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-avatar size="40" class="elevation-2">
          <v-img src="https://cdn.vuetifyjs.com/images/john.jpg"></v-img>
        </v-avatar>
      </v-app-bar>

      <!-- Main Content -->
      <v-row no-gutters class="fill-height pt-16">
        <!-- Sidebar -->
        <v-col cols="12" sm="4" md="3" lg="2">
          <v-card class="ma-2" color="grey-darken-3">
            <v-card-title class="d-flex justify-space-between align-center">
              DM Settings
              <v-btn icon>
                <v-icon>mdi-close</v-icon>
              </v-btn>
            </v-card-title>
            <v-list>
              <v-list-item-group v-model="selectedItem" color="light-blue">
                <v-list-item>
                  <v-list-item-title>DM tour guide</v-list-item-title>
                </v-list-item>
                <v-list-item>
                  <v-list-item-title>Item 1</v-list-item-title>
                </v-list-item>
                <v-list-item>
                  <v-list-item-title>Item 2</v-list-item-title>
                </v-list-item>
                <v-list-item>
                  <v-list-item-title>Item 3</v-list-item-title>
                </v-list-item>
              </v-list-item-group>
            </v-list>
            <v-subheader class="text-grey">Other Items</v-subheader>
            <v-list>
              <v-list-item>
                <v-list-item-title>Other item 1</v-list-item-title>
              </v-list-item>
              <v-list-item>
                <v-list-item-title>Other item 2</v-list-item-title>
              </v-list-item>
            </v-list>
          </v-card>
        </v-col>

        <!-- Body -->
        <v-col cols="12" sm="8" md="9" lg="10">
          <v-card class="ma-2 fill-height" color="grey-darken-3">
            <v-card-text>
              This is the body of the component.
            </v-card-text>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<script setup>
import { ref } from 'vue';

const selectedItem = ref(0);

const goBack = () => {
  // Implement your back navigation logic here
  console.log('Going back');
};
</script>

<style scoped>
.v-app-bar {
  background-color: rgba(0, 0, 0, 0.5) !important;
}
</style>