<script setup></script>

<template>
  <div class="p-4 flex items-center justify-between">
    <div class="flex items-center gap-x-4">
      <div class="w-14 h-14 rounded-full bg-gray-300"></div>
      <div class="flex flex-col">
        <NuxtLink class="hover:underline" to="/">
          <h1 class="font-semibold">Md Mofazzal Hossain</h1>
        </NuxtLink>
        <p class="text-sm opacity-75">12 May 2025</p>
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
