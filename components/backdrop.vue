<script setup>
const props = defineProps(["handleToggleModal"]);
</script>

<template>
  <div
    class="fixed top-0 left-0 w-screen h-screen bg-black/20 flex items-center justify-center overflow-hidden z-50"
    @click.self="handleToggleModal"
  >
    <slot></slot>
  </div>
</template>
