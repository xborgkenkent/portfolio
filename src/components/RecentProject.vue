<script setup lang="ts">

const props = defineProps({
  title: String,
  description: String,
  link: String,
  image: String
});

</script>

<template>
    <div class="w-fit flex flex-col border border-[#575757] p-4 rounded-md hover:bg-[#262626]">
        <img :src="`/${image}`" class="w-fit">
        <p class="font-sans font-bold text-lg text-[#FAFAFA] tracking-wide">{{ title }}</p>
        <p class="font-sans font-thin text-base text-[#666161] tracking-wide">{{ description }}</p>
    </div>
</template>