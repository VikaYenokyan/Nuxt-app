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
    <ul class="grid grid-cols-3 my-10 gap-10">
      <li class="w-full" v-for="user in users" :key="user.id">
        <UserLink :user="user"/>
      </li>
    </ul>
  </div>
</template>

<style>
h1 {
  color: red;
}
</style>