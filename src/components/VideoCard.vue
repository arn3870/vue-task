<template>
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
    <ContentWithXP :checked="checked" @update:checked="updateChecked" :xpAmount="100">
      <template #title> Watch this video </template>
      <template #description>
        Watch this video to learn more about the features.
      </template>
    </ContentWithXP>
  </v-card>
</template>

<script setup>
import ContentWithXP from './ContentWithXP.vue';

const props = defineProps({
  checked: Boolean,
});

const emit = defineEmits(['update:checked']);

const updateChecked = (newValue) => {
  emit('update:checked', newValue);
};
</script>
