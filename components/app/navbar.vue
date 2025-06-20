<script setup lang="ts">
import { Icon } from "@iconify/vue";
</script>

<template>
  <nav
    class="relative flex items-center gap-x-4 justify-between p-4 mx-auto max-w-[1200px]"
  >
    <ul>
      <li>
        <NuxtLink to="/" class="text-xl font-bold">mini facebook</NuxtLink>
      </li>
    </ul>
    <ul class="flex items-center gap-x-2 px-4">
      <AppSearch />
      <li><NuxtLink to="/profile">Profile</NuxtLink></li>
      <li>
        <NuxtLink to="/login">
          <Icon
            icon="material-symbols-light:logout-rounded"
            class="w-10 h-10 icon-button text-red-500 bg-transparent !!hover:bg-red-500/20"
        /></NuxtLink>
      </li>
    </ul>
  </nav>
</template>
