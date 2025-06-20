<script setup lang="ts">
import { Icon } from "@iconify/vue";

const router = useRouter();
const searchEl = ref<HTMLInputElement | null>(null);
const searchText = ref("");

const props = defineProps(["handleToggleShowSearch"]);

onMounted(() => {
  searchEl.value?.focus();
});

const handleSearch = () => {
  router.push({
    path: "/search",
    query: { q: searchText.value },
  });
};
</script>

<template>
  <div
    class="absolute top-0 left-0 w-full h-full z-50 bg-white justify-center flex items-center px-2 gap-x-2"
  >
    <div
      @click="handleToggleShowSearch"
      class="flex items-center justify-center"
    >
      <Icon
        icon="material-symbols-light:arrow-back-ios-rounded"
        class="w-12 h-12 icon-button"
      />
    </div>
    <form
      class="flex items-center gap-x-2 w-full"
      @submit.prevent="handleSearch"
    >
      <input
        ref="searchEl"
        type="text"
        v-model="searchText"
        placeholder="Search here..."
        class="input w-full px-4 py-2 border-1 border-black/20 rounded-full font-semibold"
      />
      <button class="btn-primary rounded-full p-1">
        <Icon
          icon="material-symbols-light:search-rounded"
          class="w-8 h-8 rounded-full text-white"
        />
      </button>
    </form>
  </div>
</template>
