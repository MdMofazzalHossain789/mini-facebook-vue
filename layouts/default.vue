<script setup>
const user = ref(null);

provide("user", user);
</script>

<template>
  <div class="w-screen h-screen">
    <div class="border-b-[1px] border-black/20 shadow-md">
      <AppNavbar></AppNavbar>
    </div>
    <main class="max-w-[1200px] mx-auto w-full h-full">
      <slot></slot>
    </main>
  </div>
</template>
