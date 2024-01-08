<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue';
import Footer from './components/Footer.vue'
</script>

<template>
  <div class="flex flex-col justify-center items-center gap-8 text-textColor">
    <div class="p-8 bg-linksColor w-full text-bgColor flex flex-row justify-center items-center gap-2">
      <h1 class="text-4xl font-bold">
      Hello, friend 
      </h1>
      <span class="material-symbols-outlined text-6xl">
        timer
      </span>
    </div>
    <HelloWorld msg="Stop Watch" />
    <Footer />
  </div>
</template>

<style scoped>

</style>
