<script setup>
import {ref, watch} from "vue";

const users = [
  {
    id: '1',
    name: 'Ian',
    email: 'ian@gmail.com'
  },
  {
    id: '2',
    name: 'Cyril',
    email: 'cyril@gmail.com'
  },
  {
    id: '3',
    name: 'Candy',
    email: 'candy@gmail.com'
  },
  {
    id: '4',
    name: 'Sam',
    email: 'sam@gmail.com'
  },
  {
    id: '5',
    name: 'Evans',
    email: 'evans@gmail.com'
  }
];

const searchQuery = ref('')

const filteredList = ref(users)

watch(searchQuery, (newValue) => {
  filteredList.value = users.filter((user) => user.name.toLowerCase().includes(newValue.toLowerCase()))
})

</script>

<template>
  <input type="text" v-model="searchQuery"/>
  <ul>
    <li v-for="user in filteredList">
      <span :key="user.id">{{ user.name }}</span>
    </li>
  </ul>
</template>

<style scoped>

</style>