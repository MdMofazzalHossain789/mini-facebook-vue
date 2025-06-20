<script setup>
import { Icon } from "@iconify/vue";
import { format } from "timeago.js";

defineProps(["author", "avatar", "createdAt"]);

const toggleShowOptions = ref(false);

const handleToggleShowOptions = () => {
  toggleShowOptions.value = !toggleShowOptions.value;
};
</script>

<template>
  <div class="px-4 py-2 flex items-center justify-between">
    <div class="flex items-center gap-x-2">
      <NuxtImg :src="avatar" class="w-10 h-10 rounded-full bg-gray-300" />
      <div class="flex flex-col">
        <NuxtLink class="hover:underline" to="/">
          <h1 class="font-semibold">{{ author }}</h1>
        </NuxtLink>
        <p class="text-sm opacity-75">{{ format(createdAt) }}</p>
      </div>
    </div>
    <div class="relative">
      <div class="icon-button relaitve" @click="handleToggleShowOptions">
        <Icon icon="material-symbols-light:more-horiz" class="w-8 h-8" />
      </div>
      <PostOptions
        v-if="toggleShowOptions"
        :handleToggleShowOptions="handleToggleShowOptions"
      />
    </div>
  </div>
</template>
