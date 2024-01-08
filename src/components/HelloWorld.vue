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
  const minutes = Math.floor(elapsedTime / 60);
  const seconds = elapsedTime % 60;
  return `${minutes}:${seconds}`
}
</script>

<template>
  <h2 class="font-semibold text-2xl">{{ msg }}</h2>
  <div class="flex flex-col justify-center items-center gap-4">
    <span>{{ formatTime(elapsedTime) }}</span>
    <div class="flex flex-row justify-center items-center gap-4">
      <button 
      v-if="state === 'stopped'" 
      @click="start">start</button>
      <button
      v-if="state === 'running'" 
      @click="pause">pause</button>
      <button 
      v-if="state === 'paused'" 
      @click="start">resume</button>
      <button 
      v-if="state === 'running' || state === 'paused'"
      @click="restart">restart</button>
    </div>
  </div>
</template>

