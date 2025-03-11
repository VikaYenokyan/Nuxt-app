<script setup>
definePageMeta({
  layout: "users",
});

const { user_id } = useRoute().params;

const { data } = await useFetch(`https://dummyjson.com/users/${user_id}`);
</script>

<template>
  <div>
    <h1 class="text-3xl font-semibold">User ID: {{ user_id }}</h1>
    <div class="flex gap-16 my-6 border-1 border-gray-300 shadow-lg p-5">
      <NuxtImg class='shrink-0 w-[272px] h-[272px]' :src="`${data.image}`" width="200" height="200" />
      <div class="flex flex-col grow-1">
        <h2 class="text-3xl font-medium">{{ data.firstName }} {{ data.lastName }}</h2>
        <div class="mt-3 flex gap-2 text-gray-700">
          <p>ID: {{ data.id }}</p>
          <p>|</p>
          <p>Age: {{ data.age }}</p>
        </div>

        <div class="mt-5 pb-2 border-b-1 border-gray-300 w-full">
          <p><span class="font-bold">Email:</span> {{ data.email }}</p>
        </div>

        <div class="mt-2 pb-2 border-b-1 border-gray-300 w-full">
          <p><span class="font-bold">Phone:</span> {{ data.phone }}</p>
        </div>

        <div class="mt-2 pb-2 border-b-1 border-gray-300 w-full">
          <p><span class="font-bold">Address:</span> {{ data.address.address }}, {{ data.address.city }}, {{ data.address.state }}, {{ data.address.postalCode }} </p>
        </div>

        <div class="mt-2 pb-2 w-full">
          <p><span class="font-bold">Company:</span> {{ data.company.name }} - {{ data.company.title }} <br> Department: {{ data.company.department }} </p>
        </div>

      </div>
    </div>
  </div>
</template>

<style>
h1 {
  color: red;
}
</style>