<script setup lang="ts">
import { defineProps, ref, computed } from 'vue'

const props = defineProps({
  name: String,
  iconName: String,
});

const isHovered = ref(false)

const iconSrc = computed(() =>
  isHovered.value ? `/hover-${props.iconName}` : `/${props.iconName}`
);
</script>

<template>
  <div
    class="flex flex-col justify-center gap-2 py-2 pt-2 items-center border-[#575757] border rounded-md hover:bg-[#262626] text-[#FAFAFA]"
    @mouseenter="isHovered = true"
    @mouseleave="isHovered = false"
  >
    <img
      :src="iconSrc"
      alt="icon"
      class="transition-transform duration-300 ease-out size-8"
      :class="{ '-translate-y-1 scale-100': isHovered }"
    />
    <p class="font-sans font-thin text-sm tracking-wide">{{ name }}</p>
  </div>
</template>
