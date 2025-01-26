<script setup lang="ts">
import { ref } from "vue";

const isMenuOpen = ref(false);

function toggleMenu() {
  isMenuOpen.value = !isMenuOpen.value;
}
</script>

<template>
  <div class="flex items-center justify-between text-[#FAFAFA] py-4 px-6">
    <!-- Logo -->
    <div>
      <p
        class="font-sans font-bold text-2xl tracking-wider hidden md:block"
      >
        KENT REGIEL
      </p>
      <p class="font-sans font-bold text-2xl tracking-wider md:hidden">
        KR
      </p>
    </div>

    <!-- Menu for large screens -->
    <div class="hidden md:flex space-x-4">
      <p class="font-mono text-base font-thin tracking-wide">about me</p>
      <p class="font-mono text-base font-thin tracking-wide">projects</p>
      <p class="font-mono text-base font-thin tracking-wide">contact</p>
    </div>

    <!-- Hamburger menu for small and medium screens -->
    <div class="md:hidden relative">
      <button @click="toggleMenu" class="focus:outline-none">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          fill="none"
          viewBox="0 0 24 24"
          stroke="currentColor"
          class="w-6 h-6"
        >
          <path
            stroke-linecap="round"
            stroke-linejoin="round"
            stroke-width="2"
            d="M4 6h16M4 12h16M4 18h16"
          />
        </svg>
      </button>
      <div
        v-if="isMenuOpen"
        class="absolute right-0 mt-2 bg-[#1A1A1A] rounded-lg shadow-lg w-48"
      >
        <ul class="flex flex-col space-y-2 py-2 px-4">
          <li class="font-mono text-base font-thin tracking-wide">
            about me
          </li>
          <li class="font-mono text-base font-thin tracking-wide">
            projects
          </li>
          <li class="font-mono text-base font-thin tracking-wide">
            contact
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<style>
</style>
