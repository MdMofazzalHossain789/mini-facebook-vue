<script setup>
const props = defineProps(["likesCount", "commentsCount", "sharesCount"]);

const comments = ref(props.commentsCount);
const likes = ref(props.likesCount);
const shares = ref(props.sharesCount);
const liked = ref(false);
const canComment = ref(false);
const commentEl = ref(null);
const comment = ref("");

onMounted(() => {
  canComment.value = false;
});

watch(canComment, async (newValue) => {
  if (newValue) {
    await nextTick();
    commentEl.value?.focus();
  }
});

const showInteraction = computed(() => {
  const parts = [];

  if (likes.value > 0) {
    parts.push(`${likes.value} like${likes.value > 1 ? "s" : ""}`);
  }

  if (comments.value > 0) {
    parts.push(`${comments.value} comment${comments.value > 1 ? "s" : ""}`);
  }

  if (shares.value > 0) {
    parts.push(`${shares.value} share${shares.value > 1 ? "s" : ""}`);
  }

  if (parts.length === 0) return "";
  if (parts.length === 1) return parts[0];
  if (parts.length === 2) return parts.join(` and `);

  return parts.slice(0, -1).join(",") + " and " + parts[parts.length - 1];
});

function handleLike() {
  liked.value = !liked.value;
  if (liked.value) {
    likes.value += 1;
  } else {
    likes.value -= 1;
  }
}

function handleSubmitComment() {
  comment.value = "";
  canComment.value = false;
  comments.value += 1;
}
</script>

<template>
  <div class="px-4 pt-4 pb-2 flex flex-col gap-y-2">
    <p v-if="showInteraction" class="flex items-center gap-x-1 opacity-70">
      {{ showInteraction }}
    </p>
    <div v-if="canComment">
      <div
        class="fixed top-0 left-0 h-screen w-screen z-0"
        @click="canComment = !canComment"
      ></div>
      <div class="relative z-10 flex items-center gap-x-4 w-full">
        <div>
          <div class="w-12 h-12 rounded-full bg-gray-300"></div>
        </div>
        <form
          class="flex items-center gap-x-4 w-full"
          @submit.prevent="handleSubmitComment"
        >
          <input
            ref="commentEl"
            v-model="comment"
            type="text"
            placeholder="Type your comment..."
            class="w-full bg-black/5 px-4 py-3 rounded-full border-[1px] border-black/20"
          />
          <button class="icon-button">
            <svg
              xmlns="http://www.w3.org/2000/svg"
              viewBox="0 0 24 24"
              fill="currentColor"
              class="size-6"
            >
              <path
                d="M3.478 2.404a.75.75 0 0 0-.926.941l2.432 7.905H13.5a.75.75 0 0 1 0 1.5H4.984l-2.432 7.905a.75.75 0 0 0 .926.94 60.519 60.519 0 0 0 18.445-8.986.75.75 0 0 0 0-1.218A60.517 60.517 0 0 0 3.478 2.404Z"
              />
            </svg>
          </button>
        </form>
      </div>
    </div>
    <div v-else class="flex items-center gap-x-4 justify-between">
      <button class="button" @click="handleLike">
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
            d="M6.633 10.25c.806 0 1.533-.446 2.031-1.08a9.041 9.041 0 0 1 2.861-2.4c.723-.384 1.35-.956 1.653-1.715a4.498 4.498 0 0 0 .322-1.672V2.75a.75.75 0 0 1 .75-.75 2.25 2.25 0 0 1 2.25 2.25c0 1.152-.26 2.243-.723 3.218-.266.558.107 1.282.725 1.282m0 0h3.126c1.026 0 1.945.694 2.054 1.715.045.422.068.85.068 1.285a11.95 11.95 0 0 1-2.649 7.521c-.388.482-.987.729-1.605.729H13.48c-.483 0-.964-.078-1.423-.23l-3.114-1.04a4.501 4.501 0 0 0-1.423-.23H5.904m10.598-9.75H14.25M5.904 18.5c.083.205.173.405.27.602.197.4-.078.898-.523.898h-.908c-.889 0-1.713-.518-1.972-1.368a12 12 0 0 1-.521-3.507c0-1.553.295-3.036.831-4.398C3.387 9.953 4.167 9.5 5 9.5h1.053c.472 0 .745.556.5.96a8.958 8.958 0 0 0-1.302 4.665c0 1.194.232 2.333.654 3.375Z"
          />
        </svg>

        {{ liked ? "Liked" : "Like" }}
      </button>
      <button class="button" @click="canComment = !canComment">
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
            d="M7.5 8.25h9m-9 3H12m-9.75 1.51c0 1.6 1.123 2.994 2.707 3.227 1.129.166 2.27.293 3.423.379.35.026.67.21.865.501L12 21l2.755-4.133a1.14 1.14 0 0 1 .865-.501 48.172 48.172 0 0 0 3.423-.379c1.584-.233 2.707-1.626 2.707-3.228V6.741c0-1.602-1.123-2.995-2.707-3.228A48.394 48.394 0 0 0 12 3c-2.392 0-4.744.175-7.043.513C3.373 3.746 2.25 5.14 2.25 6.741v6.018Z"
          />
        </svg>

        Comment
      </button>
      <button class="button">
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
            d="M7.217 10.907a2.25 2.25 0 1 0 0 2.186m0-2.186c.18.324.283.696.283 1.093s-.103.77-.283 1.093m0-2.186 9.566-5.314m-9.566 7.5 9.566 5.314m0 0a2.25 2.25 0 1 0 3.935 2.186 2.25 2.25 0 0 0-3.935-2.186Zm0-12.814a2.25 2.25 0 1 0 3.933-2.185 2.25 2.25 0 0 0-3.933 2.185Z"
          />
        </svg>

        Share
      </button>
    </div>
  </div>
</template>
