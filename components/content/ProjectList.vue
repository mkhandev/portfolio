<script setup>
const { status, data, error } = await useFetch(
  "https://api.github.com/users/mkhandev/repos"
);

</script>

<template>
  <div class="not-prose">
    <section>
      <ul class="grid grid-cols-1 gap-4">
        <li
          v-for="repository in data"
          :key="repository.id"
          class="border border-gray-200 rounded-sm p-4 hover:bg-gray-100 font-mono"
        >
          <a :href="repository.html_url" target="_blank">
            <div class="flex items-center justify-between text-sm">
              <div class="font-semibold">{{ repository.name }}</div>
              <div>{{ repository.stargazers_count }} ★</div>
            </div>
            <p class="text-sm">
              {{ repository.description }}
            </p>
          </a>
        </li>
      </ul>
    </section>
  </div>
</template>

<style></style>
