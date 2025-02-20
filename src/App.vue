<script setup lang="ts">
import Header from "./components/Header.vue"
import AboutMe from "./views/AboutMe.vue"
import { useHead } from '@vueuse/head'
import Clarity from '@microsoft/clarity';


useHead({
  script: [
    {
      innerHTML: `
        (function(c,l,a,r,i,t,y){
          c[a]=c[a]||function(){(c[a].q=c[a].q||[]).push(arguments)};
          t=l.createElement(r);t.async=1;t.src="https://www.clarity.ms/tag/"+i;
          y=l.getElementsByTagName(r)[0];y.parentNode.insertBefore(t,y);
        })(window, document, "clarity", "script", "qcr6f8k0n4");
      `,
      type: 'text/javascript'
    }
  ]
})

const projectId = "qcr6f8k0n4"

Clarity.init(projectId);


</script>

<template>
  <div class="min-h-screen flex justify-center bg-[#0a0a0a] pb-36">
    <div class="lg:w-6/12 lg:pt-10 w-full p-5 md:w-8/12 md:pt-10">
      <Header class="pb-16"/>
      <AboutMe/>
    </div>
  </div>
</template>