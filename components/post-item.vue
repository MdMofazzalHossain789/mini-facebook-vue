<script setup>
const props = defineProps(["post"]);
</script>

<template>
  <div class="card">
    <PostHeader
      :author="post.author"
      :avatar="post.avatar"
      :createdAt="post.createdAt"
    />
    <PostContent :caption="post.caption" :content="post.content" />
    <PostFooter
      :likesCount="post.likes"
      :commentsCount="post.comments"
      :sharesCount="post.shares"
    />
  </div>
</template>
