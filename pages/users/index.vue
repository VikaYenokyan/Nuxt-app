<script setup>
definePageMeta({
  layout: "users",
});

// const users = ref([
//   {
//     id: 1,
//     name: "Alex",
//   },
//   {
//     id: 2,
//     name: "Bob",
//   },
//   {
//     id: 3,
//     name: "John",
//   },
//]);

const { data } = await useFetch("https://dummyjson.com/users");

const users = ref(data.value.users);
</script>

<template>
  <div>
    <h1 class="text-3xl">All users</h1>
    <ul class="flex flex-wrap gap-5 my-10">
      <li class='bg-blue-900 text-white rounded-md p-2' v-for="user in users" :key="user.id">
        <NuxtLink :to="`/users/user-${user.id}`">{{ user.firstName }} {{ user.lastName }}</NuxtLink>
      </li>
    </ul>
  </div>
</template>

<style>
h1 {
  color: red;
}
</style>