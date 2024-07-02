<template>
  <v-col
    v-if="!props.showSidebar || $vuetify.display.smAndUp"
    cols="12"
    sm="8"
    md="9"
    lg="9"
    class="h-full"
  >
    <v-card
      class="m-2 h-full !bg-white/50 bg-opacity-50 !rounded-tl-md !rounded-tr-xl !rounded-br-xl !rounded-bl-md !overflow-y-auto hidden-scrollbar"
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
        <ProgressLinear :progress="progress" :bufferValue="bufferValue" />
        <InboxDetailCard
          :checked="inboxChecked"
          @update:checked="updateInboxChecked"
          :inboxColors="inboxColors"
        />
        <VideoCard
          :checked="videoChecked"
          @update:checked="updateVideoChecked"
        />
        <XPEarnedModal
          :model-value="showXPEarnedModal"
          :imageSrc="congratsImage"
          :xpAmount="xpAmount"
          @close="handleModalClose"
        />
        <TourCompletedModal
          v-model="showTourCompletedModal"
          :imageSrc="tourCompletedImage"
          :xpAmount="xpAmount"
        />
      </v-container>
    </v-card>
  </v-col>
</template>

<script setup>
import { ref, watch } from "vue";
import { useDisplay } from "vuetify";
import SparklingStarticon from "@/assets/Icons/SparklingStarticon.vue";
import EarningsIcons from "@/assets/Icons/EarningsIcons.vue";
import ProgressLinear from "./ProgressLinear.vue";
import InboxDetailCard from "./InboxDetailCard.vue";
import VideoCard from "./VideoCard.vue";
import XPEarnedModal from "./XPEarnedModal.vue";
import TourCompletedModal from "./TourCompletedModal.vue";

import CongratsImage from "@/assets/images/congrats.png";
import TourCompletedImage from "@/assets/images/tour_completed.png";

const props = defineProps({
  showSidebar: Boolean,
  progress: Number,
  bufferValue: Number,
  inboxColors: Array,
});

const display = useDisplay();
const showSidebar = ref(props.showSidebar);
const inboxChecked = ref(false);
const videoChecked = ref(false);
const showXPEarnedModal = ref(false);
const showTourCompletedModal = ref(false);
const xpAmount = ref(0);
const progress = ref(props.progress);

watch([inboxChecked, videoChecked], ([newInboxChecked, newVideoChecked]) => {
  if (newInboxChecked || newVideoChecked) {
    if (newInboxChecked && !newVideoChecked) {
      xpAmount.value = 500;
    } else if (!newInboxChecked && newVideoChecked) {
      xpAmount.value = 100;
    } else {
      xpAmount.value = 600;
    }
    showXPEarnedModal.value = true;
    progress.value += xpAmount.value;
  }
});

const updateInboxChecked = (value) => {
  inboxChecked.value = value;
};

const updateVideoChecked = (value) => {
  videoChecked.value = value;
};

const handleModalClose = () => {
  showXPEarnedModal.value = false;
  console.log("handle close modal", inboxChecked.value, videoChecked.value);
  if (inboxChecked.value && videoChecked.value) {
    showTourCompletedModal.value = true;
  }
};

const congratsImage = CongratsImage;
const tourCompletedImage = TourCompletedImage;
</script>
