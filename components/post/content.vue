<script setup>
const props = defineProps(["content", "caption"]);
</script>

<template>
  <div class="flex flex-col gap-y-2">
    <p class="px-4">
      {{ caption }}
    </p>

    <NuxtImg
      v-if="content"
      :src="content"
      class="w-full h-[400px] bg-gray-500 object-contain rounded-md"
    ></NuxtImg>
  </div>
</template>
