<script setup>
import { Icon } from "@iconify/vue";

const props = defineProps(["handleToggleShowOptions"]);
</script>
<template>
  <div class="">
    <Backdrop :handleToggleModal="handleToggleShowOptions"> </Backdrop>
    <div
      class="absolute top-[50%] right-[50%] z-50 card p-4 w-[200px] px-1 py-1 flex flex-col gap-y-1"
      @click.stop=""
    >
      <PostOptionItem>
        <template #icon>
          <Icon
            icon="material-symbols-light:link-rounded"
            class="w-full h-full"
          />
        </template>
        <template #default>Copy link</template>
      </PostOptionItem>
      <PostOptionItem>
        <template #icon>
          <Icon icon="material-symbols-light:remove" class="w-full h-full" />
        </template>
        <template #default>Hide</template>
      </PostOptionItem>
      <PostOptionItem>
        <template #icon>
          <Icon
            icon="material-symbols-light:edit-outline-rounded"
            class="w-full h-full"
          />
        </template>
        <template #default>Edit Post</template>
      </PostOptionItem>
      <PostOptionItem variant="danger">
        <template #icon>
          <Icon
            icon="material-symbols-light:delete-forever-outline-rounded"
            class="w-full h-full"
          />
        </template>
        <template #default>Delete post</template>
      </PostOptionItem>
    </div>
  </div>
</template>
