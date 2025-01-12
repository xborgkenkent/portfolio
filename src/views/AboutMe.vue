<script setup lang="ts">
import Tech from "../components/Tech.vue"
import RecentProject from "../components/RecentProject.vue"

interface Tech {
    name: string
    icon: string
}

const techs: Tech[] = [
{ name: 'Scala', icon: 'scala.svg' },
{ name: 'Typescript', icon: 'typescript.svg' },
{ name: 'Nuxt', icon: 'nuxt.svg' },
{ name: 'Laravel', icon: 'laravel.svg' },
{ name: 'AWS', icon: 'aws.svg' },
{ name: 'PostgreSQL', icon: 'postgresql.svg' },
{ name: 'Git', icon: 'git.svg' },
{ name: 'Docker', icon: 'docker.svg' },
{ name: 'OpenAI', icon: 'openai.svg' },
  { name: 'Vue.js', icon: 'vuejs.svg' },
  { name: 'Tailwind', icon: 'tailwind.svg' },
  { name: 'CSS3', icon: 'css3.svg' },
  ]
</script>

<template>
    <div class="flex flex-col text-[#FAFAFA]">
        <img src="../../public/cover1.png" class="size-full transition-transform duration-300 ease-out hover:scale-105">
        <div class="pt-2 flex">
            <div class="relative">
                <img src="../../public/profile.jpg" class="size-24 rounded-full border-4 border-[#575757]">
                <div class="absolute inset-0 rounded-full border-4 border-transparent hover:border-t-[#4CAF50] hover:border-l-[#4CAF50] hover:border-r-[#4CAF50]  transition-all duration-1000 ease-in-out hover:rotate-[420deg]"></div>
            </div>
            <div class="flex flex-col pl-6 pt-2 gap-2">
                <div class="flex justify-center items-center">
                    <p class="font-sans font-bold text-2xl text-[#FAFAFA] tracking-wider">Hey, I'm Kent</p>
                    <p class="text-2xl hover:animate-wave">👋</p>
                </div>
                <div class="flex items-center gap-2">
                    <p class="text-xs">📍</p>
                    <p class="font-sans font-thin text-base text-[#666161] tracking-wide">Cebu City, Philippines</p>
                </div>
            </div>
        </div>
        <p class="font-sans font-thin text-base pt-8 tracking-wide">I’m an experienced full-stack developer with a specialization in back-end development, complemented  by extensive  expertise in system automation and seamless integrations.</p>
        <div class="grid grid-cols-4 gap-3 pt-8">
        <div v-for="(tech, index) in techs" :key="index">
            <Tech :name="tech.name" :icon-name="tech.icon" />
        </div>
    </div>
        <div class="flex flex-col gap-2 pt-20">
            <p class="font-sans font-thin text-md text-[#666161] tracking-wide">Recent Projects</p>
            <div class="flex gap-3 justify-between">
                <RecentProject/>
                <RecentProject/>
            </div>
            <div class="flex items-center gap-2">
                <p class="font-sans font-bold text-md text-[#FAFAFA] tracking-wide">More projects</p>
                <img src="../../public/right-arrow.svg" class="size-4">
            </div>
        </div>
    </div>
</template>