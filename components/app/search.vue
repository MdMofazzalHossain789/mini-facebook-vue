<script setup>
import { Icon } from "@iconify/vue";

const toggleShowSearch = ref(false);

const handleToggleShowSearch = () => {
  toggleShowSearch.value = !toggleShowSearch.value;
};
</script>

<template>
  <div>
    <div
      @click="handleToggleShowSearch"
      v-if="!toggleShowSearch"
      class="icon-button"
    >
      <Icon icon="material-symbols-light:search-rounded" class="w-8 h-8" />
    </div>
    <div v-else>
      <div class="" @click.stop="">
        <AppSearchInput />
      </div>
      <div
        class="fixed z-20 left-0 top-0 h-full w-full"
        @click.self="handleToggleShowSearch"
      ></div>
    </div>
  </div>
</template>
