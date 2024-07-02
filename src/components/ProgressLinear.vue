<template>
  <v-progress-linear
    :model-value="progress"
    color="primary"
    height="10"
    rounded
    :buffer-value="bufferValue"
    bg-color="white"
    bg-opacity="100"
  >
  </v-progress-linear>
</template>

<script setup>
const props = defineProps({
  progress: Number,
  bufferValue: Number,
});
</script>

<style scoped>
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
</style>
