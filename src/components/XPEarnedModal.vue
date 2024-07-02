<template>
  <v-dialog :modelValue="modelValue" @update:modelValue="updateModel" max-width="463px">
    <v-card class="!rounded-[25px]">
      <v-card-text>
        <img :src="imageSrc" alt="Congratulations" class="mx-auto my-4" />
        <div class="text-center text-lg font-bold">
          Congratulations You've Earned
        </div>
        <div class="text-center text-2xl gradient-text font-bold my-2">
          {{ xpAmount }} XP
        </div>
        <v-btn @click="closeModal" class="gradient-button !rounded-xl my-4" block>
          Continue
        </v-btn>
      </v-card-text>
    </v-card>
  </v-dialog>
</template>

<script setup>
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

const emit = defineEmits(['close']);

const updateModel = (value) => {
  emit('close', value);
};

const closeModal = () => {
  emit('close', false);
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
