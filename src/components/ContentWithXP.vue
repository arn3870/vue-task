<template>
  <div class="flex flex-col w-full">
    <div class="flex !justify-start items-center">
      <div class="flex-grow">
        <v-radio-group v-model="internalChecked" hide-details>
          <v-radio
            :false-icon="FalseRadioIcon"
            :true-icon="TrueRadioIcon"
            :value="true"
          >
            <template v-slot:label>
              <h4 :class="{ 'line-through': internalChecked }">
                <slot name="title" />
              </h4>
            </template>
          </v-radio>
        </v-radio-group>
      </div>
      <div class="flex !justify-between text-[16px] font-bold">
        <div class="gradient-text">
          <v-icon
            v-if="internalChecked"
            :icon="checkedIcon"
            width="150px"
          ></v-icon>
          <span v-else class="mr-1">+</span>
          <span class="mr-2">500</span>
          <span class="text-xs">XP</span>
        </div>
      </div>
    </div>
    <p class="text-[12px] font-medium !text-[#8C8D90]">
      <slot name="description" />
    </p>
  </div>
</template>

<script setup>
import { ref, watch } from "vue";
import FalseRadioIcon from "@/assets/Icons/FalseRadioIcon.vue";
import TrueRadioIcon from "@/assets/Icons/TrueRadioIcon.vue";
import checkedIcon from "@/assets/Icons/checkedIcon.vue";

const props = defineProps({
  checked: Boolean,
});

const emit = defineEmits(["update:checked"]);

const internalChecked = ref(props.checked);

watch(internalChecked, (newValue) => {
  emit("update:checked", newValue);
});
</script>
