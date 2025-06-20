<script setup>
import { Icon } from "@iconify/vue";

const props = defineProps(["handleToggleModal"]);
</script>

<template>
  <div
    class="flex items-center gap-x-2 w-full py-3 pl-4 pr-2 card cursor-pointer"
    @click="handleToggleModal"
  >
    <div>
      <div class="w-10 h-10 bg-gray-500 rounded-full"></div>
    </div>
    <div
      class="w-full rounded-full bg-black/5 py-2 border-[1px] border-black/10 flex items-center px-4 text-sm opacity-70"
    >
      What's on your mind...
    </div>
    <div class="p-2">
      <Icon
        icon="material-symbols-light:add-photo-alternate-outline-rounded"
        class="w-6 h-6 opacity-70"
      />
    </div>
  </div>
</template>
