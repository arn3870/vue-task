<template>
  <v-col v-if="showSidebar" cols="12" sm="4" md="3" lg="3" class="h-full">
    <v-card
      class="m-2 h-full bg-white py-4 px-4 !rounded-tl-lg !rounded-tr-md !rounded-br-md !rounded-bl-lg !overflow-y-auto hidden-scrollbar"
    >
      <v-card-title
        class="!flex justify-between items-center font-bold text-base leading-6 text-[#514F5F]"
      >
        DM Settings
        <v-btn
          :icon="CrossIcon"
          density="compact"
          flat
          rounded="lg"
          variant="outlined"
          color="#F4F7F8"
        ></v-btn>
      </v-card-title>
      <v-list>
        <v-subheader class="text-gray-500 text-[10px] font-bold pl-4"
          >MANAGE INBOX</v-subheader
        >
        <v-list-item
          v-for="(item, index) in listItems"
          :key="index"
          :value="index"
          @click="item.title === 'DM tour guide' ? toggleView() : null"
        >
          <template v-slot:prepend>
            <v-icon :icon="item.icon" color="#7E7D84" class="mr-4"></v-icon>
          </template>
          <v-list-item-title class="!text-[14px] !font-bold">{{
            item.title
          }}</v-list-item-title>
        </v-list-item>
      </v-list>
      <v-subheader class="text-gray-500 text-[10px] font-bold pl-4 !pr-3"
        >ADVANCED MESSAGES</v-subheader
      >
      <v-list>
        <v-list-item
          v-for="(item, index) in otherItems"
          :key="index"
          class="opacity-50 pointer-events-none"
        >
          <template v-slot:prepend>
            <v-icon :icon="item.icon" class="mr-3"></v-icon>
          </template>
          <v-list-item-title>
            <span class="flex justify-between">
              <span class="!text-[14px] !font-bold"> {{ item.title }}</span>
              <span class="!text-[10px] !font-600">Coming soon... </span>
            </span>
          </v-list-item-title>
        </v-list-item>
      </v-list>
    </v-card>
  </v-col>
</template>

<script setup>
import { ref } from "vue";
import CrossIcon from "@/assets/Icons/CrossIcon.vue";

const props = defineProps({
  showSidebar: Boolean,
  toggleView: Function,
  listItems: Array,
  otherItems: Array,
});
</script>

<style scoped>
.v-list-item__spacer {
  display: none !important;
}
</style>
