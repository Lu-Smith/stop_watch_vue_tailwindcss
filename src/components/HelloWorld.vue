<script setup lang="ts">
import { ref } from 'vue';
defineProps<{ msg: string }>();

const state = ref<"stopped" | "running" | "paused">("stopped");
const elapsedTime = ref<number>(0);
const interval = ref<number | undefined>(undefined);

function start() {
  state.value = "running";
  interval.value = setInterval(( ) => {
    elapsedTime.value ++
  }, 1000);
}

function pause() {
  state.value = "paused";
  clearInterval(interval.value);
}

function restart() {
  state.value = "stopped";
  clearInterval(interval.value);
  interval.value = undefined;
  elapsedTime.value = 0;
}

function formatTime(elapsedTime: number) {
  const minutes = `0${Math.floor(elapsedTime / 60)}`.slice(-2);
  const seconds = `0${elapsedTime % 60}`.slice(-2);
  return `${minutes}:${seconds}`
}
</script>

<template>
  <h2 class="font-semibold text-2xl mt-8">{{ msg }}</h2>
  <div class="flex flex-col justify-center items-center gap-4">
    <span class="hover:bg-addColor px-8 py-14 rounded-full text-4xl
    bg-textColor border-addColor transition-all duration-300 ease-in-out
    border-spacing-2 hover:border-linksColor border-8 text-bgColor">{{ formatTime(elapsedTime) }}</span>
    <div class="flex flex-row justify-center items-center gap-4 mt-4">
      <button 
      class="bg-linksColor px-4 py-2 text-bgColor hover:bg-addColor rounded transition-all duration-300
      ease-in-out drop-shadow-md hover:filter-none font-semibold"
      v-if="state === 'stopped'"
      @click="start">start</button>
      <button
      class="bg-linksColor px-4 py-2 text-bgColor hover:bg-addColor rounded transition-all duration-300
      ease-in-out drop-shadow-md hover:filter-none font-semibold"
      v-if="state === 'running'" 
      @click="pause">pause</button>
      <button 
      class="bg-linksColor px-4 py-2 text-bgColor hover:bg-addColor rounded transition-all duration-300
      ease-in-out drop-shadow-md hover:filter-none font-semibold"
      v-if="state === 'paused'" 
      @click="start">resume</button>
      <button 
      class="bg-textColor px-4 py-2 text-bgColor hover:bg-addColor rounded transition-all duration-300
      ease-in-out drop-shadow-md hover:filter-none"
      v-if="state === 'running' || state === 'paused'"
      @click="restart">restart</button>
    </div>
  </div>
</template>

