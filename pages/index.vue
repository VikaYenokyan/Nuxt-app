<script setup>
const { data } = await useFetch("/api/example", {
  method: "post",
  body: { name: "Alex", id: 1 },
});
</script>

<template>
  <div>
    <h1 class="text-3xl">Home page</h1>
    <div
      class="mt-2 bg-blue-100 border border-blue-200 text-sm text-blue-800 rounded-lg p-4 dark:bg-blue-800/10 dark:border-blue-900 dark:text-blue-500"
      role="alert"
      tabindex="-1"
      aria-labelledby="hs-soft-color-info-label"
    >
      {{ data.msg }}
    </div>
  </div>
</template>

<style>
h1 {
  color: red;
}
</style>