<script setup>
import { Icon } from "@iconify/vue";
const props = defineProps(["likesCount", "commentsCount", "sharesCount"]);

const comments = ref(props.commentsCount);
const likes = ref(props.likesCount);
const shares = ref(props.sharesCount);
const liked = ref(false);
const showCommentInput = ref(false);
const commentEl = ref(null);
const comment = ref("");
const canSubmitComment = computed(() => {
  return comment.value === "";
});

onMounted(() => {
  showCommentInput.value = false;
});

watch(showCommentInput, async (newValue) => {
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

  return parts.slice(0, -1).join(", ") + " and " + parts[parts.length - 1];
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
  showCommentInput.value = false;
  comments.value += 1;
}
</script>

<template>
  <div class="px-2 pt-2 pb-1 flex flex-col gap-y-2">
    <p
      v-if="showInteraction"
      class="flex items-center gap-x-1 opacity-70 text-xs"
    >
      {{ showInteraction }}
    </p>
    <div v-if="showCommentInput">
      <div
        class="fixed top-0 left-0 h-screen w-screen z-0"
        @click="showCommentInput = !showCommentInput"
      ></div>
      <div class="relative z-10 flex items-center gap-x-2 w-full py-1">
        <NuxtImg
          :src="`https://i.pravatar.cc/150?img=${Math.floor(
            Math.random() * 50 + 1
          )}`"
          class="w-10 h-10 rounded-full bg-gray-300"
        ></NuxtImg>
        <form
          class="flex items-center gap-x-2 w-full"
          @submit.prevent="handleSubmitComment"
        >
          <input
            ref="commentEl"
            v-model="comment"
            type="text"
            placeholder="Type your comment..."
            class="w-full bg-black/5 px-3 py-2 rounded-full border-[1px] border-black/20"
            :class="{
              'outline-blue-500 border-blue-500 ring-blue-500':
                !canSubmitComment,
            }"
          />
          <button
            class="icon-button btn-primary text-white"
            :disabled="canSubmitComment"
          >
            <Icon
              icon="material-symbols-light:send-outline-rounded"
              class="w-6 h-6"
            />
          </button>
        </form>
      </div>
    </div>
    <div v-else class="flex items-center gap-x-1 justify-between text-sm">
      <button
        @click="handleLike"
        :class="{
          button: true,
          'text-blue-500 font-semibold transition': liked,
        }"
      >
        <Icon
          :icon="
            liked
              ? 'material-symbols-light:thumb-up-rounded'
              : 'material-symbols-light:thumb-up-outline'
          "
          class="w-6 h-6"
        />

        {{ liked ? "Liked" : "Like" }}
      </button>
      <button class="button" @click="showCommentInput = !showCommentInput">
        <Icon
          icon="material-symbols-light:comment-outline-rounded"
          class="w-6 h-6"
        />

        Comment
      </button>
      <button class="button">
        <Icon icon="material-symbols-light:share-outline" class="w-6 h-6" />

        Share
      </button>
    </div>
  </div>
</template>
