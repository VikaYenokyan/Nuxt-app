<script setup>
const name = ref("");
const email = ref("");
const message = ref("");
const isSub = ref(false);
const resultMessage = ref("");

const submitForm = async () => {
  isSub.value = true;
  resultMessage.value = "";

  const { error } = await useFetch("/api/contacts", {
    method: "post",
    body: {
      name: name.value,
      email: email.value,
      message: message.value,
    },
  });

  if (error.value) {
    resultMessage.value = "Error: " + error.value;
  } else {
    resultMessage.value = "All is success !";
    name.value = "";
    email.value = "";
    message.value = "";
    isSub.value = false;
  }
};
</script>

<template>
  <div>
    <h1 class="text-3xl">Contacts</h1>
  </div>

  <form @submit.prevent="submitForm" class="mt-10">
    <input
      required
      type="text"
      id="name"
      v-model="name"
      placeholder="Enter name"
      class="w-full border border-gray-300 rounded-2xl p-5"
    /><br />
    <input
      required
      type="email"
      id="email"
      v-model="email"
      placeholder="Enter email"
      class="w-full border border-gray-300 rounded-2xl p-5 mt-3"
    /><br />
    <textarea
      required
      type="message"
      id="message"
      v-model="message"
      placeholder="Enter message"
      class="w-full border border-gray-300 rounded-2xl p-5 mt-3"
    ></textarea
    ><br />
    <button
      type="submit"
      :disabled="isSub"
      class="mt-5 rounded-2xl bg-blue-600 px-5 py-3 text-white text-2xl"
    >
      {{ isSub ? "Отправляем..." : "Отправить" }}
    </button>
  </form>

  <div
    v-if="resultMessage"
    class="mt-5 bg-teal-100 border border-teal-200 text-sm text-teal-800 rounded-lg p-4 dark:bg-teal-800/10 dark:border-teal-900 dark:text-teal-500"
    role="alert"
    tabindex="-1"
    aria-labelledby="hs-soft-color-success-label"
  >
    {{ resultMessage }}
  </div>
</template>

<style>
h1 {
  color: red;
}
</style>