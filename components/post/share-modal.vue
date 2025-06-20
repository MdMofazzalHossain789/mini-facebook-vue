<script setup>
import { Icon } from "@iconify/vue";

const props = defineProps(["handleToggleShareModal"]);

const linkText = ref("http://localhost:3000/");
const inputRef = ref(null);

const isCopied = ref(false);

const handleCopy = () => {
  inputRef.value?.select();
  navigator.clipboard.writeText(linkText.value);
  isCopied.value = true;

  setTimeout(() => {
    isCopied.value = false;
  }, 2000);
};
</script>

<template>
  <Backdrop :handle-toggle-modal="handleToggleShareModal">
    <div class="card w-[500px] flex items-center justify-center px-4 py-6">
      <div class="flex items-center gap-x-2 w-full">
        <h1 class="min-w-fit">Shared Link</h1>
        <input
          ref="inputRef"
          type="text"
          :value="linkText"
          class="input w-full px-4 py-2"
        />
        <div @click="handleCopy">
          <Icon
            :icon="
              isCopied
                ? 'material-symbols-light:check-rounded'
                : 'material-symbols-light:content-copy-outline-rounded'
            "
            class="w-10 h-10"
            :class="{
              'icon-button': !isCopied,
              'text-green-500 p-2': isCopied,
            }"
          />
        </div>
      </div>
    </div>
  </Backdrop>
</template>
