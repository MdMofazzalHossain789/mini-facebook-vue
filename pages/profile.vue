<template>
  <div class="w-full h-full flex flex-col gap-y-2 px-4">
    <div class="pt-4 sticky top-20">
      <div class="flex flex-col gap-y-1 card p-4">
        <div class="flex items-center gap-x-4">
          <div class="w-24 h-24 bg-gray-500 rounded-full min-w-24"></div>
          <div>
            <div>
              <h1 class="font-semibold">Md Mofazzal Hossain</h1>
              <p>@mofazzal789</p>
            </div>
          </div>
        </div>
        <p class="pt-4 text-center">This is my new account</p>
      </div>
    </div>
    <div class="h-full w-full flex flex-col gap-y-2">
      <!-- About -->
      <div class="card p-4">
        <h1 class="font-semibold">About</h1>
      </div>

      <!-- Create Post -->
      <PostCreate />

      <!-- Posts -->
      <div class="sticky top-20 card">
        <h1 class="p-4 font-semibold">Posts</h1>
      </div>
    </div>
  </div>
</template>
