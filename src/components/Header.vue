<template>
  <v-app-bar app flat color="transparent" class="px-4">
    <v-btn
      :icon="BackArrowIcon"
      @click="toggleView"
      density="compact"
      rounded="lg"
      style="background-color: rgba(23, 82, 101, 0.05)"
    ></v-btn>
    <v-toolbar-title class="ml-2 text-[16px] font-bold">{{ "Messages" }}</v-toolbar-title>
    <v-spacer></v-spacer>
    <v-avatar size="40" class="shadow-md">
      <v-img src="https://cdn.vuetifyjs.com/images/john.jpg"></v-img>
    </v-avatar>
  </v-app-bar>
</template>

<script setup>
import BackArrowIcon from "@/assets/Icons/BackArrowIcon.vue";

const props = defineProps({
  toggleView: Function
});
</script>

<style scoped>
.v-toolbar-title {
  margin-left: 8px;
  font-size: 16px;
  font-weight: bold;
}
</style>
