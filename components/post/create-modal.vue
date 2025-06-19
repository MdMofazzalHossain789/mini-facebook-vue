<script setup>
const props = defineProps(["handleToggleModal"]);
const posts = inject("posts");

const postText = ref("");
const inputEl = ref(null);
const canSubmit = computed(() => {
  return postText.value === "";
});

onMounted(() => {
  inputEl.value?.focus();
});

const handleSubmitPost = () => {
  const dpNo = Math.floor(Math.random() * 10) + 1;
  const likes = Math.floor(Math.random() * 50) + 1;
  const comments = Math.floor(Math.random() * 20) + 1;
  const shares = Math.floor(Math.random() * 10) + 1;
  const id = new Date().getTime();

  posts.value.unshift({
    id,
    createdAt: new Date(Date.now()),
    author: "Anonymous",
    avatar: `https://i.pravatar.cc/150?img=${dpNo}`,
    caption: postText.value,
    likes,
    comments,
    shares,
  });

  postText.value = "";
  props.handleToggleModal();
};
</script>

<template>
  <div
    class="relative z-20 p-4 card w-full max-w-[600px] flex flex-col gap-y-4"
    @click.stop
  >
    <h1 class="text-center font-semibold text-xl opacity-50">Create A Post</h1>
    <div class="h-[1px] w-full bg-black/10"></div>
    <form
      class="flex flex-col items-center gap-y-4"
      @submit.prevent="handleSubmitPost"
    >
      <textarea
        ref="inputEl"
        v-model="postText"
        type="text"
        placeholder="What's on your mind?"
        class="w-full bg-black/5 border-1 rounded-md border-black/20 p-4 text-lg input max-h-[400px]"
      ></textarea>
      <button
        class="text-lg py-2 w-full text-center bg-blue-500 text-white font-semibold rounded-md btn-primary"
        :disabled="canSubmit"
      >
        Post
      </button>
    </form>
  </div>
</template>
