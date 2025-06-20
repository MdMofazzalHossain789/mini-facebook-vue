<template>
  <div class="min-h-screen p-4 space-y-10">
    <h1 class="text-2xl">Smooth Keyboard Scroll Fix</h1>

    <div v-for="n in 10" :key="n">
      <input
        type="text"
        class="w-full p-3 border border-gray-400 rounded"
        placeholder="Tap here..."
        @focus="handleFocus"
        @blur="handleBlur"
      />
    </div>

    <p class="text-gray-600 mt-10">
      Try focusing and blurring input fields while scrolling on a mobile device.
    </p>
  </div>
</template>

<script setup>
import { ref } from "vue";

const previousScrollY = ref(0);

// Custom smooth scroll function using requestAnimationFrame
function smoothScrollTo(targetY, duration = 500) {
  const startY = window.scrollY;
  const distance = targetY - startY;
  const startTime = performance.now();

  function step(currentTime) {
    const elapsed = currentTime - startTime;
    const progress = Math.min(elapsed / duration, 1); // Clamp to [0,1]

    // Ease out function
    const ease = 1 - Math.pow(1 - progress, 3); // Cubic easing
    window.scrollTo(0, startY + distance * ease);

    if (progress < 1) {
      requestAnimationFrame(step);
    }
  }

  requestAnimationFrame(step);
}

const handleFocus = () => {
  previousScrollY.value = window.scrollY;
};

const handleBlur = () => {
  // Delay to let keyboard close completely
  setTimeout(() => {
    smoothScrollTo(previousScrollY.value, 600); // Smoother than native `behavior: smooth`
  }, 150);
};
</script>

<style>
html,
body {
  scroll-behavior: auto !important; /* Avoid conflict with native smooth scroll */
}
</style>
