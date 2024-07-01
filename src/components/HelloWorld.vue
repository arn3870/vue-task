<template>
  <v-app>
    <v-container fluid class="py-4 px-2 h-full bg-[#e8eaf9]">
      <!-- Header -->
      <v-app-bar app flat color="transparent" class="px-4">
        <v-btn
          :icon="BackArrowIcon"
          @click="toggleView"
          density="compact"
          rounded="lg"
          style="background-color: rgba(23, 82, 101, 0.05)"
        ></v-btn>
        <!-- <v-toolbar-title class="ml-2">{{ showSidebar ? 'DM Settings' : 'Messages' }}</v-toolbar-title> -->
        <v-toolbar-title class="ml-2 text-[16px] font-bold">{{
          "Messages"
        }}</v-toolbar-title>
        <v-spacer></v-spacer>
        <v-avatar size="40" class="shadow-md">
          <v-img src="https://cdn.vuetifyjs.com/images/john.jpg"></v-img>
        </v-avatar>
      </v-app-bar>

      <!-- Main Content -->
      <v-row no-gutters class="h-full pt-16">
        <!-- Sidebar -->
        <v-col v-if="showSidebar" cols="12" sm="4" md="3" lg="3" class="h-full">
          <v-card
            class="m-2 h-full bg-white py-4 px-4 !rounded-tl-lg !rounded-tr-md !rounded-br-md !rounded-bl-lg"
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
                  <v-icon
                    :icon="item.icon"
                    color="#7E7D84"
                    class="mr-4"
                  ></v-icon>
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
                    <span class="!text-[14px] !font-bold">
                      {{ item.title }}</span
                    >
                    <span class="!text-[10px] !font-600">Coming soon... </span>
                  </span>
                </v-list-item-title>
              </v-list-item>
            </v-list>
          </v-card>
        </v-col>

        <!-- Body -->
        <v-col
          v-if="!showSidebar || $vuetify.display.smAndUp"
          cols="12"
          sm="8"
          md="9"
          lg="9"
        >
          <v-card
            class="m-2 h-full !bg-white/50 bg-opacity-50 !rounded-tl-md !rounded-tr-xl !rounded-br-xl !rounded-bl-md"
          >
            <v-container class="!w-full lg:!w-1/2">
              <div class="d-flex align-center mb-4">
                <v-icon
                  color="primary"
                  class="mr-2"
                  :icon="SparklingStarticon"
                ></v-icon>
                <span class="text-h6 font-weight-bold gradient-text"
                  >Get Started</span
                >
                <v-spacer></v-spacer>
                <div class="flex flex-row text-start">
                  <v-icon :icon="EarningsIcons" size="30px"></v-icon>
                  <div class="flex flex-col text-start">
                    <span class="text-[14px] font-bold gradient-text"
                      >You earned 20 500</span
                    >
                    <span class="text-[10px] font-bold"
                      >Total XP to earn : 12 000</span
                    >
                  </div>
                </div>
              </div>

              <v-progress-linear
                v-model="progress"
                color="primary"
                height="10"
                rounded
                :buffer-value="bufferValue"
                bg-color="white"
                bg-opacity="100"
              >
                <template v-slot:default="{ value }"> </template>
              </v-progress-linear>

              <v-card
                class="!flex !flex-col !justify-center !items-center mt-6 rounded-xl bg-white !py-10 !px-[21px]"
              >
                <v-card class="mt-6 rounded-xl inbox_detail_card w-fit">
                  <v-card-text>
                    <div class="text-h6 mb-2">Inbox Name</div>
                    <v-sheet color="white" class="pa-2 mb-4 !rounded-[10px]">
                      VivaTech
                    </v-sheet>
                    <div class="text-body-1 mb-2">Inbox Colors</div>
                    <div class="flex gap-5">
                      <v-tooltip
                        v-for="(color, index) in inboxColors"
                        :key="index"
                        location="top"
                      >
                        <template v-slot:activator="{ props }">
                          <div class="icon-wrapper" v-bind="props">
                            <v-icon
                              :color="color"
                              :icon="InboxIcon"
                              class="mr-2 transition-transform duration-200 hover:scale-125"
                            >
                            </v-icon>
                          </div>
                        </template>
                        <div class="tooltip-content">
                          <div class="flex flex-col">
                            <div>
                              <v-chip
                                :prepend-icon="InboxIcon"
                                color="white"
                                :style="{ backgroundColor: color }"
                              >
                                Vivatech
                              </v-chip>
                            </div>
                            <span class="ml-2"
                              >Hello
                              <span class="font-bold"> {FirstName}</span> it was
                              <br />pleasure to meet you</span
                            >
                          </div>
                        </div>
                      </v-tooltip>
                    </div>
                  </v-card-text>
                </v-card>
                <div class="flex flex-col w-full">
                  <div class="flex !justify-start">
                    <div
                      class="flex !justify-between w-full text-[16px] font-bold mt-6"
                    >
                      <h4>Create more inbox</h4>
                      <div>
                        <v-icon :icon="checkedIcon" width="150px"></v-icon>
                        <span class="gradient-text">500xp</span>
                      </div>
                    </div>
                  </div>
                  <p class="text-[12px] font-medium !text-[#8C8D90]">
                    Create more inbox, welcome your new contact by a message
                  </p>
                </div>
              </v-card>
              <v-card
                class="!flex !flex-col !justify-center !items-center mt-6 rounded-xl bg-white !py-10 !px-[21px]"
              >
                <v-card class="mt-6 rounded-xl w-full">
                  <v-card-text class="pa-0">
                    <video width="100%" controls>
                      <source src="../assets/video.mp4" type="video/mp4" />
                      Your browser does not support the video tag.
                    </video>
                  </v-card-text>
                </v-card>
                <div class="flex flex-col w-full">
                  <div class="flex mt-6">
                    <div
                      class="flex !justify-between w-full text-[16px] font-bold"
                    >
                      <h4>Create more inbox</h4>
                      <div>
                        <span class="gradient-text">+ 500xp</span>
                      </div>
                    </div>
                  </div>
                  <p class="text-[12px] font-medium !text-[#8C8D90]">
                    Create more inbox, welcome your new contact by a message
                  </p>
                </div>
              </v-card>
            </v-container>
          </v-card>
        </v-col>
      </v-row>
    </v-container>
  </v-app>
</template>

<script setup>
import { ref } from "vue";
import { useDisplay } from "vuetify";
import AdressBookIcon from "@/assets/Icons/AdressBookIcon.vue";
import BackArrowIcon from "@/assets/Icons/BackArrowIcon.vue";
import BlurredDMIcon from "@/assets/Icons/BlurredDMIcon.vue";
import BoostDMIcon from "@/assets/Icons/BoostDMIcon.vue";
import DiscussionRulesIcon from "@/assets/Icons/DiscussionRulesIcon.vue";
import DMStepsIcon from "@/assets/Icons/DMStepsIcon.vue";
import InboxIcon from "@/assets/Icons/InboxIcon.vue";
import SparklingStarticon from "@/assets/Icons/SparklingStarticon.vue";
import ZapierIcon from "@/assets/Icons/ZapierIcon.vue";
import CrossIcon from "@/assets/Icons/CrossIcon.vue";
import checkedIcon from "@/assets/Icons/checkedIcon.vue";
import EarningsIcons from "@/assets/Icons/EarningsIcons.vue";

const display = useDisplay();
const showSidebar = ref(true);
const selectedItem = ref(0);

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

const goBack = () => {
  // Implement your back navigation logic here
  console.log("Going back");
};
</script>

<style>
.v-list-item__spacer {
  display: none !important;
}
.gradient-text {
  background: linear-gradient(
    91.74deg,
    #40bebe -20.8%,
    #2361e6 101.14%
  ) !important;
  -webkit-background-clip: text !important;
  -webkit-text-fill-color: transparent !important;
}

.v-progress-linear {
  border-radius: 5px;
  overflow: hidden;
}

.v-progress-linear__determinate {
  background: linear-gradient(
    91.74deg,
    #40bebe -20.8%,
    #2361e6 101.14%
  ) !important;
}

.v-progress-linear__buffer {
  opacity: 0.3;
}
.inbox_detail_card {
  background: linear-gradient(
    180deg,
    #dbe5fe -0.19%,
    rgba(177, 197, 249, 0) 100.19%
  ) !important;
}
.icon-wrapper {
  display: inline-block;
  cursor: pointer;
}

.tooltip-content {
  display: flex;
  align-items: center;
  padding: 4px 8px;
  background-color: rgba(97, 97, 97, 0.9);
  border-radius: 4px;
  color: white;
  font-size: 12px;
}
</style>
