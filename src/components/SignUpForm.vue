<script setup lang="ts">
import {computed, ref} from "vue";

const form = ref({
  name: '',
  email: '',
  password: ''
})

const isValid = computed(() => {
  return form.value.name.length > 0 && form.value.email.length > 0 && form.value.password.length > 6
})

const emit = defineEmits(['submit'])

const submitHandler = (e) => {
  e.preventDefault()
  emit("submit", form.value)
}
</script>

<template>
  <form @submit="submitHandler">
    <div>
      <label for="name">Name:</label>
      <input type="text" v-model="form.name"/>
      <p v-if="form.name.length < 0">Name is a required field</p>
    </div>

    <div>
      <label for="email">Email:</label>
      <input type="email" v-model="form.email"/>
      <p v-if="form.email.length < 0">Email is a required field</p>
    </div>

    <div>
      <label for="password">Password:</label>
      <input type="password" v-model="form.password"/>
      <p v-if="form.password.length < 6">Password is a required field, at least 6 characters</p>
    </div>
    <button type="submit" :disabled="!isValid">Submit</button>
  </form>
</template>

<style scoped>

</style>