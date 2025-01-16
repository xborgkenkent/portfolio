<script setup lang="ts">
import { ref } from "vue"
import Tech from "../components/Tech.vue"
import RecentProject from "../components/RecentProject.vue"
import Modal from "../components/Modal.vue"

export interface Tech {
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

export interface Project {
    title: string
    description: string
    link: string
    image: string
    tech: Array<string>
    hasSource: boolean
}

const projects: Project[] = [
    { title: 'Finance Anomaly Detection', description: 'Live Dashboard of Anomaly Detection' , link: 'https://github.com/xborgkenkent/TikTikToe', image: 'anomaly-detection.png', tech: ['Scala', 'Apache Spark', 'Postgresql', 'JFrame'], hasSource: false},
    { title: 'Tik-Tik Toe', description: 'A tic tac toe with a twist' , link: 'https://tik-tik-toe-ten.vercel.app/', image: 'tiktiktoe.png', tech: ['Vue.js', 'Typescript', 'Tailwind CSS'], hasSource: true},
    { title: 'Kent\'s portfolio', description: 'A simple portfolio' , link: 'https://github.com/xborgkenkent/TikTikToe', image: 'portfolio.png', tech:['Vue.js', 'Typescript', 'Tailwind CSS'], hasSource: true}
    ]

    const modalTrigger = ref(false)
const selectedProject = ref<Project | null>(null)

const openModal = (project: Project) => {
    selectedProject.value = project
    modalTrigger.value = true
}

const closeModal = () => {
    modalTrigger.value = false
    selectedProject.value = null
}

</script>

<template>
    <div class="flex flex-col text-[#FAFAFA]">
        <Modal v-if="modalTrigger" ref="modalTrigger">
            <button @click="closeModal" class="px-4 py-2">
                ❌
            </button>
            <div class="flex flex-row gap-4 px-4 pb-4 text-center">
                <template v-if="selectedProject">
                    <div class="flex flex-col items-start gap-5 w-full">
                        <img :src="`../../public/${selectedProject.image}`" :alt="selectedProject.title" class="w-82 rounded-lg">
                        <h2 class="text-xl font-bold">{{ selectedProject.title }}</h2>
                        <p>{{ selectedProject.description }}</p>
                        <div class="flex justify-between items-center w-full">
                            <div class="flex items-center">
                                <a v-show="selectedProject.hasSource" :href="selectedProject.link" target="_blank" class="rounded-full text-sm font-bold text-white">
                                    <div class="flex gap-2 items-center">
                                        <img src="../../public/github.svg" :alt="selectedProject.title" class="w-8 rounded-lg">
                                        <p>Github Link</p>
                                    </div>
                                </a>    
                            </div>
                            <div class="flex items-center gap-2">
                                <div v-for="(tech, index) in selectedProject.tech" :key="index">
                                    <div class="flex bg-[#666161] p-2 rounded-lg hover:bg-[#575757]">
                                        <p>{{ tech }}</p>
                                    </div>
                                </div>
                            </div>
                        </div>
                    </div>
                </template>
            </div>
        </Modal>
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
        <p class="font-sans font-thin text-base pt-8 tracking-wide">I’m an experienced full-stack developer specializing in back-end development and big data engineering, with extensive expertise in system automation and integrations.</p>
        <div class="grid grid-cols-4 gap-3 pt-8">
            <div v-for="(tech, index) in techs" :key="index">
                <Tech :name="tech.name" :icon-name="tech.icon" />
            </div>
        </div>
        <div class="flex flex-col gap-2 pt-20">
            <p class="font-sans font-thin text-md text-[#575757] tracking-wide">Recent Projects</p>
            <div class="columns-1 sm:columns-1 lg:columns-2 gap-4">
            <div v-for="(project, index) in projects" :key="index" class="mb-4 break-inside-avoid">
                <RecentProject 
                    @click="openModal(project)"
                    :title="project.title" 
                    :description="project.description" 
                    :link="project.link" 
                    :image="project.image" 
                />
            </div>
        </div>

            <div class="flex items-center gap-2 pt-6">
              <p class="font-sans font-bold text-md text-[#FAFAFA] tracking-wide">More projects</p>
              <img src="../../public/right-arrow.svg" class="size-4">
            </div>
          </div>
          
        <div class="flex flex-col items-center justify-center pt-24 gap-5">
            <p class="font-sans font-bold text-6xl text-[#FAFAFA] tracking-wider">LET'S TALK</p>
            <div class="flex gap-2">
                <img src="../../public/linkedin.svg" class="size-8">
                <img src="../../public/github.svg" class="size-8">
            </div>
            <p class="font-sans font-thin text-md text-[#FAFAFA] tracking-wider">kentregiel.buncal139@gmail.com</p>
        </div>
    </div>
</template>