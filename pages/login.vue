<script setup>
definePageMeta({
  layout: false,
});

const username = ref("");
const password = ref("");
const user = inject("user");

const handleSubmit = () => {
  user.value = {
    username: username.value,
  };
};
</script>

<template>
  <div class="w-screen h-screen flex items-center justify-center">
    <div class="card p-4 w-full max-w-[50%]">
      <div class="py-4">
        <h1 class="text-xl font-semibold text-center">Log In</h1>
        <p class="text-xs text-center opacity-70">
          Provide an username and password to continue.
        </p>
      </div>
      <form @submit.prevent="handleSubmit">
        <div class="flex flex-col gap-y-4">
          <label class="flex flex-col gap-y-2">
            Username
            <input
              type="text"
              class="input py-2 px-4 rounded-md"
              v-model="username"
            />
          </label>
          <label class="flex flex-col gap-y-2">
            Password
            <input
              type="text"
              class="input py-2 px-4 rounded-md"
              v-model="password"
            />
          </label>
          <button
            class="btn-primary px-4 py-2 rounded-md text-white font-semibold"
          >
            Log In
          </button>
          <p class="text-xs opacity-70 text-center">
            You can log in with dummy username and password
          </p>
        </div>
      </form>
    </div>
  </div>
</template>
