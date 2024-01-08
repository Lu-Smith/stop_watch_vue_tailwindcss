<script setup lang="ts">
import { ref } from 'vue';
defineProps<{ msg: string }>();

const timeElappsed = ref(0);
const interval = ref<number | undefined>(undefined);

function start() {
  interval.value = setInterval(( ) => {
    timeElappsed.value ++
  }, 1000);
}

function pause() {
  clearInterval(interval.value);
}
</script>

<template>
  <h2 class="font-semibold text-2xl">{{ msg }}</h2>
  <div class="flex flex-col justify-center items-center gap-4">
    <span>{{ timeElappsed }}</span>
    <div class="flex flex-row justify-center items-center gap-4">
      <button @click="start">start</button>
      <button @click="pause">pause</button>
      <button>restart</button>
    </div>
  </div>
</template>

