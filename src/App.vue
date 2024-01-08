<script setup lang="ts">
import HelloWorld from './components/HelloWorld.vue';
import Footer from './components/Footer.vue'
</script>

<template>
  <div class="flex flex-col justify-center items-center gap-4 text-textColor">
    <h1 class="bg-linksColor w-full text-bgColor p-8 text-4xl font-bold">
    Hello, friend 🐥
    </h1>
    <HelloWorld msg="Stop Watch" />
    <Footer />
  </div>
</template>

<style scoped>

</style>
