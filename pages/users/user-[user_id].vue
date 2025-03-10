<script setup>
const { user_id } = useRoute().params;
definePageMeta({
  layout: "users",
});
</script>

<template>
  <div>
    <h1 class="text-3xl">ID of user: {{ user_id }}</h1>
  </div>
</template>

<style>
h1 {
  color: red;
}
</style>