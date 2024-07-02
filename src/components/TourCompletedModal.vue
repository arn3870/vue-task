<template>
  <v-dialog
    :modelValue="modelValue"
    @update:modelValue="updateModel"
    max-width="463px"
  >
    <v-card class="rounded-25px">
      <v-card-text>
        <img :src="imageSrc" alt="Tour Completed" class="mx-auto my-4" />
        <div class="text-center text-lg font-bold">
          Congratulations You’ve completed
        </div>
        <div class="text-center gradient-text text-2xl font-bold my-2">
          DM Tour guide
        </div>
        <div class="flex justify-center items-center gap-8">
          <div class="font-bold text-[#7E7D84]">Total XP earned</div>
          <div class="gradient-text flex gap-2 items-center">
            <div class="flex items-center">
              <v-icon :icon="checkedIcon" width="150px"></v-icon>
              <span>{{ xpAmount }}</span>
            </div>
            <v-icon :icon="diamondIcon"></v-icon>
          </div>
        </div>
        <v-btn
          @click="closeModal"
          class="gradient-button !rounded-xl my-4"
          block
        >
          Done
        </v-btn>
      </v-card-text>
    </v-card>
  </v-dialog>
</template>

<script setup>
import checkedIcon from "@/assets/Icons/checkedIcon.vue";
import diamondIcon from "@/assets/Icons/DiamondIcon.vue";
const props = defineProps({
  modelValue: Boolean,
  xpAmount: {
    type: Number,
    required: true,
  },
  imageSrc: {
    type: String,
    required: true,
  },
});

const emit = defineEmits(["update:modelValue"]);

const updateModel = (value) => {
  emit("update:modelValue", value);
};

const closeModal = () => {
  emit("update:modelValue", false);
};
</script>

<style scoped>
.rounded-25px {
  border-radius: 25px !important;
}
.gradient-button {
  background: linear-gradient(
    91.74deg,
    #40bebe -20.8%,
    #2361e6 101.14%
  ) !important;
  color: white;
}
</style>
