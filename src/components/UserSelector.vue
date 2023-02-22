<script setup lang="ts">
import { ref } from 'vue';

type User = {
  name: string;
  profpicSrc: string;
};
const users: User[] = [
  {
    name: 'tika-m',
    profpicSrc: 'https://cdn-icons-png.flaticon.com/512/3153/3153346.png',
  },
  {
    name: 'garlic-naan',
    profpicSrc: 'https://cdn-icons-png.flaticon.com/512/9436/9436138.png',
  },
];
const selectedUserName = ref<string>('tika-m');

const onUserSelected = (user: User) => {
  selectedUserName.value = user.name;
};
</script>

<template>
  <div class="bg-very-dark-purple py-20 px-28 flex flex-col items-center">
    <h1 class="text-light-gray text-xl font-bold text-center">
      Who is playing now?
    </h1>
    <div class="flex flex-row flex-wrap mt-9 gap-6 justify-center">
      <button
        v-for="user in users"
        :key="user.name"
        @click="onUserSelected(user)"
        class="
          bg-dark-purple
          py-12
          flex flex-col
          items-center
          rounded-lg
          text-light-gray
          hover:text-white
          min-w-[150px]
          border
          hover:border-light-gray
        "
        :class="{ 'border-light-grey': user.name === selectedUserName, 'border-transparent': user.name !== selectedUserName }"
      >
        <img :src="user.profpicSrc" class="aspect-square w-14" />
        <span class="text-xs font-bold mt-6">{{ user.name }}</span>
      </button>

      <button
        class="
          bg-dark-purple
          py-12
          flex flex-col
          items-center
          rounded-lg
          text-blue
          hover:text-light-blue
          min-w-[150px]
          max-w-[150px]
        "
      >
        <span
          class="
            rounded-full
            border border-dark-gray-blue
            text-xl
            px-2
            my-6
          "
          >+</span
        >
        <span class="text-xs font-bold mt-auto">Add user</span>
      </button>
    </div>
    <button
      class="
        text-blue
        hover:text-light-blue
        mt-14
        rounded-full
        border border-dark-gray-blue
        hover:border-blue
        py-3
        px-10
        text-sm
      "
    >
      Manage users
    </button>
  </div>
</template>
