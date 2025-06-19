<script setup>
import { format } from "timeago.js";

defineProps(["author", "avatar", "createdAt"]);
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
    <div class="icon-button">
      <svg
        xmlns="http://www.w3.org/2000/svg"
        fill="none"
        viewBox="0 0 24 24"
        stroke-width="1.5"
        stroke="currentColor"
        class="size-6"
      >
        <path
          stroke-linecap="round"
          stroke-linejoin="round"
          d="M6.75 12a.75.75 0 1 1-1.5 0 .75.75 0 0 1 1.5 0ZM12.75 12a.75.75 0 1 1-1.5 0 .75.75 0 0 1 1.5 0ZM18.75 12a.75.75 0 1 1-1.5 0 .75.75 0 0 1 1.5 0Z"
        />
      </svg>
    </div>
  </div>
</template>
