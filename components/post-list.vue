<script setup>
const posts = inject("posts");
</script>

<template>
  <div class="px-4">
    <PostCreate />
  </div>
  <div class="flex flex-col gap-y-2 p-4">
    <PostItem v-for="post in posts" :key="post.id" :post="post" />
  </div>
</template>
