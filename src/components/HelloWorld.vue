<script setup lang="ts">
import { ref } from 'vue';
defineProps<{ msg: string }>();

const timeElappsed = ref(0);

function start() {
  const interval = setInterval(( ) => {

  }, 1000)
}
</script>

<template>
  <h2 class="font-semibold text-2xl">{{ msg }}</h2>
  <div class="flex flex-col justify-center items-center gap-4">
    <span>00:00</span>
    <div class="flex flex-row justify-center items-center gap-4">
      <button @click="start">start</button>
      <button>pause</button>
      <button>restart</button>
    </div>
  </div>
</template>

