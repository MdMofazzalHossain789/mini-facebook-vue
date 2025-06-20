<script setup>
defineProps(["handleToggleModal"]);
</script>

<template>
  <div class="">
    <Backdrop :handleToggleModal="handleToggleModal"> </Backdrop>
    <div
      class="absolute top-[50%] right-[50%] z-50 card p-4 w-[200px] px-1 py-1 flex flex-col gap-y-1"
      @click.stop=""
    >
      <slot>Options Content</slot>
    </div>
  </div>
</template>
