<script setup lang="ts">
import Header from "./components/Header.vue"
import AboutMe from "./views/AboutMe.vue"
</script>

<template>
  <div class="min-h-screen flex justify-center bg-[#0a0a0a] pb-36">
    <div class="lg:w-6/12 lg:pt-10 w-full p-5 md:w-8/12 md:pt-10">
      <Header class="pb-16"/>
      <AboutMe/>
    </div>
  </div>
</template>