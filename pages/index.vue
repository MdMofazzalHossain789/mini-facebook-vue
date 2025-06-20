<script setup>
import { ref, provide } from "vue";

const posts = ref([
  {
    id: 1,
    createdAt: new Date(Date.now() - 1000 * 60 * 60 * 1), // 1 hour ago
    author: "Md Mofazzal Hossain",
    avatar: "https://i.pravatar.cc/150?img=1",
    caption: "Exploring Vue 3 with provide/inject 🚀",
    content: "https://i.pravatar.cc/150?img=2",
    likes: 25,
    comments: 12,
    shares: 4,
  },
  {
    id: 2,
    createdAt: new Date(Date.now() - 1000 * 60 * 60 * 3), // 3 hours ago
    author: "Sadia Anjum",
    avatar: "https://i.pravatar.cc/150?img=2",
    caption: "Loving the Composition API!",
    content: null,
    likes: 40,
    comments: 8,
    shares: 10,
  },
  {
    id: 3,
    createdAt: new Date(Date.now() - 1000 * 60 * 60 * 24), // 1 day ago
    author: "Rafiul Hasan",
    avatar: "https://i.pravatar.cc/150?img=3",
    caption: "Just finished a new project in Vue 🔥",
    content: null,
    likes: 33,
    comments: 10,
    shares: 2,
  },
  {
    id: 4,
    createdAt: new Date(Date.now() - 1000 * 60 * 60 * 48), // 2 days ago
    author: "Ayesha Noor",
    avatar: "https://i.pravatar.cc/150?img=4",
    caption: "Learning to use provide/inject like a pro.",
    content: null,
    likes: 18,
    comments: 5,
    shares: 1,
  },
  {
    id: 5,
    createdAt: new Date(Date.now() - 1000 * 60 * 60 * 72), // 3 days ago
    author: "Jamal Uddin",
    avatar: "https://i.pravatar.cc/150?img=5",
    caption: "Frontend development is fun 😄",
    content: null,
    likes: 50,
    comments: 25,
    shares: 15,
  },
  {
    id: 6,
    createdAt: new Date(Date.now() - 1000 * 60 * 30), // 30 minutes ago
    author: "Rumana Aktar",
    avatar: "https://i.pravatar.cc/150?img=6",
    caption: "What's your favorite Vue feature?",
    content: null,
    likes: 22,
    comments: 6,
    shares: 3,
  },
  {
    id: 7,
    createdAt: new Date(Date.now() - 1000 * 60 * 60 * 6), // 6 hours ago
    author: "Nahid Islam",
    avatar: "https://i.pravatar.cc/150?img=7",
    caption: "Building reusable components today!",
    content: null,
    likes: 35,
    comments: 20,
    shares: 6,
  },
  {
    id: 8,
    createdAt: new Date(Date.now() - 1000 * 60 * 60 * 10), // 10 hours ago
    author: "Fatema Begum",
    avatar: "https://i.pravatar.cc/150?img=8",
    caption: "Dark mode or light mode? 🤔",
    content: null,
    likes: 19,
    comments: 3,
    shares: 1,
  },
  {
    id: 9,
    createdAt: new Date(Date.now() - 1000 * 60 * 60 * 168), // 7 days ago
    author: "Shakil Khan",
    avatar: "https://i.pravatar.cc/150?img=9",
    caption: "Finally launched my first portfolio site!",
    content: null,
    likes: 45,
    comments: 18,
    shares: 12,
  },
  {
    id: 10,
    createdAt: new Date(Date.now() - 1000 * 60 * 60 * 2), // 2 hours ago
    author: "Nadia Sultana",
    avatar: "https://i.pravatar.cc/150?img=10",
    caption: "Animation in Vue is so smooth!",
    content: null,
    likes: 29,
    comments: 14,
    shares: 8,
  },
]);

provide("posts", posts);
</script>

<template>
  <div class="">
    <PostList />
  </div>
</template>
