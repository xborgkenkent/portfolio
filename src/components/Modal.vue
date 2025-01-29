<script setup lang="ts">

</script>

<template>
    <div class="fixed inset-0 bg-black/50 flex z-50">
        <div class="w-11/12 md:w-10/12 lg:w-fit fixed top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 bg-[#1A1A1A] rounded-lg z-[100]">
        <slot></slot>
        </div>
    </div>
</template>