<script setup lang="ts">
import Search from "./search.vue";
</script>

<template>
  <nav
    class="flex items-center gap-x-4 justify-between p-4 mx-auto max-w-[1200px]"
  >
    <ul>
      <li>
        <NuxtLink to="/" class="text-xl font-bold">mini facebook</NuxtLink>
      </li>
    </ul>
    <ul class="flex items-center gap-x-4 px-4">
      <Search />
      <li><NuxtLink to="/profile">Profile</NuxtLink></li>
      <li><button href="#">Logout</button></li>
    </ul>
  </nav>
</template>
