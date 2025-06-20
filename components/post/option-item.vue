<script setup>
const props = defineProps({
  variant: {
    type: String,
    default: "default",
  },
});

const variantClass = computed(() => {
  switch (props.variant) {
    case "danger":
      return "text-red-500 hover:bg-red-100";
    default:
      return "hover:bg-black/5";
  }
});
</script>

<template>
  <div
    class="flex gap-x-2 rounded-md px-3 py-2 cursor-pointer min-w-fit items-center"
    :class="variantClass"
  >
    <div class="w-6 h-6">
      <slot name="icon"></slot>
    </div>
    <div>
      <div class="text-sm capitalize">
        <slot></slot>
      </div>
      <div class="text-xs opacity-70">
        <slot name="description"></slot>
      </div>
    </div>
  </div>
</template>
