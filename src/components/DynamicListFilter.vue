<script setup>
import {computed, ref} from "vue";

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

const filteredList = computed(() => {
  return users.filter((user) => user.name.toLowerCase().includes(searchQuery.value.toLowerCase()))
})

</script>

<template>
  <input type="text" v-model="searchQuery"/>
  <ul>
    <li v-for="user in filteredList">
      <div :key="user.id">
        <h3>Name: <span >{{ user.name }}</span></h3>
        <h3>Email: <span>{{ user.email}}</span></h3>
      </div>
    </li>
  </ul>
</template>

<style scoped>

</style>