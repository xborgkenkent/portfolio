<script setup lang="ts">

</script>

<template>
    <div class="fixed inset-0 bg-black/50 flex z-50">
        <div class="fixed top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 bg-[#1A1A1A] rounded-lg w-fit mx-4 z-[100]">
        <slot></slot>
        </div>
    </div>
</template>