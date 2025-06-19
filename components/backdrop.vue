<script setup>
const props = defineProps(["handleToggleModal"]);
</script>

<template>
  <div
    class="fixed top-0 left-0 w-screen h-screen bg-black/20 z-1 flex items-center justify-center"
    @click="handleToggleModal"
  >
    <slot></slot>
  </div>
</template>
