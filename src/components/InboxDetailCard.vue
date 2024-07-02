<template>
  <v-card class="!flex !flex-col !justify-center !items-center mt-6 rounded-xl bg-white !py-10 !px-[21px]">
    <img :src="GroupInbox" alt="Inbox" />
    <ContentWithXP :checked="checked" @update:checked="updateChecked" :xpAmount="500">
      <template #title>
        Create more inbox
      </template>
      <template #description>
        Create more inbox, welcome your new contact by a message
      </template>
    </ContentWithXP>
  </v-card>
</template>

<script setup>
import GroupInbox from '@/assets/images/GroupInbox.png';
import ContentWithXP from './ContentWithXP.vue';

const props = defineProps({
  checked: Boolean,
});

const emit = defineEmits(['update:checked']);

const updateChecked = (newValue) => {
  emit('update:checked', newValue);
};
</script>
