<script setup>
const user = ref(null);

provide("user", user);
</script>

<template>
  <div class="w-screen h-screen">
    <div
      class="bg-white border-b-[1px] border-black/20 shadow-md fixed top-0 left-0 w-full z-40"
    >
      <AppNavbar></AppNavbar>
    </div>
    <main class="max-w-[500px] mx-auto w-full h-full pt-[130px]">
      <div
        class="z-30 fixed top-[90px] left-4 right-4 h-10 text-center p-4 rounded-md border-1 border-red-500 bg-red-100 text-red-700 mb-2 text-xs flex items-center justify-center"
      >
        It's just a front end design right now.
      </div>
      <slot></slot>
    </main>
  </div>
</template>
