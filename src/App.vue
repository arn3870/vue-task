<template>
  <v-app>
    <v-container fluid class="py-4 px-2 h-full bg-[#e8eaf9]">
      <Header :toggleView="toggleView" />
      <v-row no-gutters class="h-full pt-16">
        <Sidebar :showSidebar="showSidebar" :toggleView="toggleView" :listItems="listItems" :otherItems="otherItems" />
        <MainContent :showSidebar="showSidebar" :progress="progress" :bufferValue="bufferValue" :inboxColors="inboxColors" />
      </v-row>
    </v-container>
  </v-app>
</template>

<script setup>
import { ref } from 'vue';
import { useDisplay } from 'vuetify';
import Header from './components/Header.vue';
import Sidebar from './components/Sidebar.vue';
import MainContent from './components/MainContent.vue';

import SparklingStarticon from "@/assets/Icons/SparklingStarticon.vue";
import InboxIcon from "@/assets/Icons/InboxIcon.vue";
import DiscussionRulesIcon from "@/assets/Icons/DiscussionRulesIcon.vue";
import AdressBookIcon from "@/assets/Icons/AdressBookIcon.vue";
import ZapierIcon from "@/assets/Icons/ZapierIcon.vue";
import BoostDMIcon from "@/assets/Icons/BoostDMIcon.vue";
import BlurredDMIcon from "@/assets/Icons/BlurredDMIcon.vue";

const display = useDisplay();
const showSidebar = ref(true);

const toggleView = () => {
  if (display.smAndDown.value) {
    showSidebar.value = !showSidebar.value;
  }
};

const listItems = [
  { title: "DM tour guide", icon: SparklingStarticon },
  { title: "Inbox", icon: InboxIcon },
  { title: "Discussion Rules", icon: DiscussionRulesIcon },
  { title: "Adress Book", icon: AdressBookIcon },
  { title: "Zapier", icon: ZapierIcon },
];

const otherItems = [
  { title: "Boost DM®", icon: BoostDMIcon },
  { title: "Blurred DM®", icon: BlurredDMIcon },
];

const progress = ref(30);
const bufferValue = ref(30);
const inboxColors = [
  "#DB4CF4",
  "#8057EC",
  "#2864ED",
  "#10BBE0",
  "#EF3A00",
  "#EFBB00",
  "#93ADB2",
];
</script>
