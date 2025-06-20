<script setup>
import { Icon } from "@iconify/vue";

const route = useRoute();
const searchText = computed(() => route.query.q);
</script>

<template>
  <div class="flex flex-col gap-y-2 pt-2 w-full">
    <div class="flex items-center justify-between">
      <div class="card p-4 text-lg flex items-center justify-between w-full">
        <p>
          Search results for
          <span class="font-semibold line-clamp-1">"{{ searchText }}"</span>
        </p>
        <div
          class="flex items-center justify-baseline gap-x-2 text-sm font-semibold py-2 hover:bg-black/5 cursor-pointer rounded-md px-4 min-w-fit"
        >
          <Icon
            icon="material-symbols-light:sort-rounded"
            class="w-6 h-6 border-1 border-black/20 rounded-md"
          />
          Sorted by
        </div>
      </div>
    </div>
    <div></div>
  </div>
</template>
