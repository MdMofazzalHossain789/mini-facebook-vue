<script setup>
import { Icon } from "@iconify/vue";

const props = defineProps(["handleToggleShowOptions"]);
</script>
<template>
  <OptionList :handleToggleModal="handleToggleShowOptions">
    <OptionItem>
      <template #icon>
        <Icon
          icon="material-symbols-light:link-rounded"
          class="w-full h-full"
        />
      </template>
      <template #default>Copy link</template>
    </OptionItem>
    <OptionItem>
      <template #icon>
        <Icon icon="material-symbols-light:remove" class="w-full h-full" />
      </template>
      <template #default>Hide</template>
    </OptionItem>
    <OptionItem>
      <template #icon>
        <Icon
          icon="material-symbols-light:edit-outline-rounded"
          class="w-full h-full"
        />
      </template>
      <template #default>Edit </template>
    </OptionItem>
    <OptionItem variant="danger">
      <template #icon>
        <Icon
          icon="material-symbols-light:delete-forever-outline-rounded"
          class="w-full h-full"
        />
      </template>
      <template #default>Delete </template>
    </OptionItem></OptionList
  >
</template>
