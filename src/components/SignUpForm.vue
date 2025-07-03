<script setup lang="ts">
import {computed, ref} from "vue";

const form = ref({
  name: '',
  email: '',
  password: ''
})

const isValid = computed(() => {
  return form.value.name.length > 0 && form.value.email.length > 0 && form.value.password.length >= 6
})

const emit = defineEmits(['submit'])

const submitHandler = (e) => {
  e.preventDefault()
  emit("submit", form.value)
}
</script>

<template>
  <form @submit="submitHandler">
    <div :style="{
      color: form.name.length <= 0 ? 'red': 'black'
    }">
      <label for="name">Name:</label>
      <input id='name' type="text" v-model="form.name"/>
      <p v-if="form.name.length <= 0">Name is a required field</p>
    </div>

    <div :style="{
      color: form.email.length <= 0 ? 'red': 'black'
    }">
      <label for="email">Email:</label>
      <input id='email' type="email" v-model="form.email"/>
      <p v-if="form.email.length <= 0">Email is a required field</p>
    </div>

    <div :style="{
      color: form.password.length < 6 ? 'red': 'black'
    }">
      <label for="password">Password:</label>
      <input id='password' type="password" v-model="form.password"/>
      <p v-if="form.password.length < 6">Password is a required field, at least 6 characters</p>
    </div>
    <button type="submit" :disabled="!isValid">Submit</button>
  </form>
</template>

<style scoped>

</style>