<script setup lang="ts">
import { Icon } from "@iconify/vue";

const searchEl = ref(null);
const searchText = ref("");

onMounted(() => {
  searchEl.value?.focus();
});

const handleSearch = () => {
  console.log(searchText.value);
};
</script>

<template>
  <div
    class="absolute top-0 left-0 w-full h-full z-50 bg-white flex justify-center"
  >
    <form
      class="flex items-center gap-x-2 px-4 w-full"
      @submit.prevent="handleSearch"
    >
      <input
        ref="searchEl"
        type="text"
        v-model="searchText"
        placeholder="Search here..."
        class="input w-full px-4 py-2 border-1 border-black/20 rounded-full"
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
