<script setup>
const toggleModal = ref(false);

function handleToggleModal() {
  console.log(toggleModal.value);
  toggleModal.value = !toggleModal.value;
}
</script>

<template>
  <Backdrop v-if="toggleModal" :handleToggleModal="handleToggleModal">
    <PostCreateModal :handleToggleModal="handleToggleModal" />
  </Backdrop>
  <PostCreateUi :handleToggleModal="handleToggleModal" />
</template>
