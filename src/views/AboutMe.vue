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
    { name: 'Node.js', icon: 'node.svg' },
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
    // { title: 'Finance Anomaly Detection', description: 'Live Dashboard of Anomaly Detection' , link: 'https://github.com/xborgkenkent/TikTikToe', image: 'anomaly-detection.png', tech: ['Scala', 'Apache Spark', 'Postgresql', 'JFrame'], hasSource: false},
    { title: 'Sentiment Analysis Live Dashboard', description: 'This simulation creates a sample Twitter post to check its tone—whether it is positive, negative, or neutral. It is useful for studying how computers understand emotions in text.' , link: '', image: 'sentiment.png', tech:['Laravel', 'Apache Spark', 'Vue.js', 'Node.js', 'Typescript', 'Tailwind CSS'], hasSource: false},
    { title: 'Tik-Tik Toe', description: 'This is a unique take on Tic-Tac-Toe! Instead of ending when you get three in a row, the game continues, letting you score points for each match you make. Once the match ends, the player with the most points wins!' , link: 'https://tik-tik-toe-ten.vercel.app/', image: 'tiktiktoe.png', tech: ['Vue.js', 'Typescript', 'Tailwind CSS'], hasSource: false},
    { title: 'Kent\'s portfolio', description: 'A simple portfolio.' , link: 'https://github.com/xborgkenkent/TikTikToe', image: 'portfolio.png', tech:['Vue.js', 'Typescript', 'Tailwind CSS'], hasSource: false}
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

const hoverProfile = ref(false)
const hoveredSection = ref<string | null>(null)

const highlightSection = (section: string) => {
  hoveredSection.value = section
}

const resetHighlight = () => {
  hoveredSection.value = null
}
</script>

<template>
    <div class="flex flex-col text-[#FAFAFA]">
        <Transition 
          enter-active-class="transition-all ease-in duration-200"
          leave-active-class="transition-all ease-out duration-200"
          enter-from-class="opacity-0"
          leave-to-class="opacity-0"
          mode="out-in"
        >
            <Modal v-if="modalTrigger" ref="modalTrigger">
                <button @click="closeModal" class="px-4 py-2">
                    ❌
                </button>
                <div class="flex flex-row gap-4 px-4 pb-4 text-center">
                    <template v-if="selectedProject">
                        <div class="flex flex-col items-start gap-5 w-full">
                            <img 
                              :src="`/${selectedProject.image}`" 
                              :alt="selectedProject.title" 
                              class="w-full rounded-lg">
                            <h2 class="text-xl font-bold">{{ selectedProject.title }}</h2>
                            <p>{{ selectedProject.description }}</p>
                            <div class="flex flex-col justify-between w-fit gap-2">
                                <div class="flex items-center">
                                    <a 
                                      v-show="selectedProject.hasSource" 
                                      :href="selectedProject.link" target="_blank" 
                                      class="rounded-full text-sm font-bold text-white">
                                         <div class="flex gap-2 items-center">
                                            <img 
                                              src="../../public/github.svg" 
                                              :alt="selectedProject.title" 
                                              class="w-8 rounded-lg">
                                            <p>Github Link</p>
                                        </div>
                                    </a>    
                                </div>
                                <div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 items-center gap-2">
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
        </Transition>
        <img src="../../public/cover1.png" class="size-full transition-transform duration-300 ease-out hover:scale-105">
        <div class="pt-2 flex">
            <div class="relative">
                <img src="../../public/profile.jpg" class="size-24 rounded-full border-4 border-[#575757]">
                <div 
                  @mouseover="hoverProfile = true" 
                  @mouseleave="hoverProfile = false"  
                  class="absolute inset-0 rounded-full border-4 border-transparent hover:border-t-[#4CAF50] hover:border-l-[#4CAF50] hover:border-r-[#4CAF50]  transition-all duration-1000 ease-in-out hover:rotate-[420deg]">
                </div>
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
        <p 
          class="font-sans font-thin text-base pt-8 tracking-wide" 
          :class="[ 
              hoverProfile ? 'text-[#666161] font-normal' : 'text-[#FAFAFA]' 
            ]">
            I'm an experienced 
          <span 
            class="transition-all duration-100"
            :class="[
              hoverProfile ? 'transition-transform duration-1000 ease-linear bg-orange-400 text-[#FAFAFA] p-1 font-normal' : 'text-[#FAFAFA]'
            ]"
          >
            full-stack developer
          </span>specializing in
          <span 
            class="transition-all duration-100"
            :class="[
              hoverProfile  ? 'transition-transform duration-1000 ease-linear bg-orange-400 text-[#FAFAFA] p-1 font-normal' : 'text-[#FAFAFA]'
            ]"
          >
          back-end development
          </span> , with extensive expertise in 
          <span 
            class="transition-all duration-100"
            :class="[
              hoverProfile  ? 'transition-transform duration-1000 ease-linear bg-orange-400 text-[#FAFAFA] p-1 font-normal' : 'text-[#FAFAFA]'
            ]"
          >
            system automation
          </span> and 
          <span 
            class="transition-all duration-100"
            :class="[
              hoverProfile ? 'transition-transform duration-1000 ease-linear bg-orange-400 text-[#FAFAFA] p-1 font-normal' : 'text-[#FAFAFA]'
            ]"
          >
            integrations
          </span>.
        </p>
        <div class="grid lg:grid-cols-3 md:grid-cols-2 grid-cols-1 gap-3 pt-8">
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

            <!-- <div class="flex items-center gap-2 pt-6">
              <p class="font-sans font-bold text-md text-[#FAFAFA] tracking-wide">More projects</p>
              <img src="../../public/right-arrow.svg" class="size-4">
            </div> -->
          </div>
          
        <div class="flex flex-col items-center justify-center pt-24 gap-5">
            <p class="font-sans font-bold text-6xl text-[#FAFAFA] tracking-wider">LET'S TALK</p>
            <div class="flex gap-2">
              <a href="https://www.linkedin.com/in/kent-regiel-buncal/" target="_blank" class="text-2xl hover:animate-wave">
                <img src="../../public/linkedin.svg" class="size-8">
              </a>
              <a href="https://github.com/xborgkenkent" target="_blank" class="text-2xl hover:animate-wave">
                <img src="../../public/github.svg" class="size-8">
              </a>
            </div>
            <p class="font-sans font-thin text-md text-[#FAFAFA] tracking-wider">kentregiel.buncal139@gmail.com</p>
        </div>
    </div>
</template>