<script setup>
const showNextModelLabel = ref(false);
const colorMode = useColorMode();

const modes = ["system", "light", "dark"];

const nextModeIcons = {
  system: "🌓",
  light: "🌕",
  dark: "🌑",
};

const nextMode = computed(() => {
  const currentModeIndex = modes.indexOf(colorMode.preference);
  let nextModeIndex = null;

  if (currentModeIndex + 1 == modes.length) {
    nextModeIndex = 0;
  } else {
    nextModeIndex = currentModeIndex + 1;
  }

  return modes[nextModeIndex];
});

const toggleMode = () => colorMode.preference = nextMode.value;


const nextModeIcon = computed(() => nextModeIcons[nextMode.value])
</script>

<template>
  <div class="flex space-x-2 items-center">
    <div class="text-gray-500 text-xs" v-if="showNextModelLabel">Change to {{ nextMode }}</div>
    <button
        @mouseenter="showNextModelLabel = true"
        @mouseleave="showNextModelLabel = false"
      @click="toggleMode"
      class="hover:bg-gray-200 dark:hover:bg-gray-600 px-2 py-1 text-gray-500"
    >
      {{ nextModeIcon }}
    </button>
  </div>
</template>

<style></style>
