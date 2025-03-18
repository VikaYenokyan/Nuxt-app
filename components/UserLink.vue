<script setup>
const { user } = defineProps(["user"]);
</script>

<template>
  <div class="p-5 border-amber-950 border flex flex-col">
    <NuxtImg :src="`${user.image}`" class="w-full"/>
    <h2 class="text-3xl">{{ user.firstName }} {{ user.lastName }}</h2>
    <p class="mt-2 text-3xl text-gray-700">Age: {{ user.age }}</p>
    <NuxtLink class="mt-5 text-2xl" :to="`mailto:${user.email}`"><b>Email:</b> {{ user.email }}</NuxtLink>
    <NuxtLink class='rounded-2xl bg-blue-600 px-5 py-3 text-white text-xl inline-flex mt-5 w-max ml-auto' :to="`/users/user-${user.id}`"
      >View profile</NuxtLink
    >
  </div>
</template>

<style></style>