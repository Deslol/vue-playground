<script setup lang="ts">

import {computed, onBeforeMount, onMounted, reactive, Ref, ref} from "vue";

interface JSONSchema {
  name: string,
  label: string,
  type: 'text' | 'email' | 'password' | 'number',
  required: boolean,
}

interface formState extends JSONSchema {
  input: string;
}

const props = defineProps<{
  schema: JSONSchema[]
}>()

const emit = defineEmits<{
  (e: 'submit', value: formState[]): void
}>()

const isValid = computed(() => {
  return state.value.every((item: formState) => {
    if (!item.required) return true
    return item.required && item.input.length > 0
  })
})

const errors = computed(() => state.value.map((item: formState) => ({
  [item.name]: item.input.length === 0 ? `${item.name} is a required field` : ''
})))

const state: Ref<formState[]> = ref([])

onBeforeMount(() => {
  // initialise the variable for storing the state.
  props.schema.forEach((item) => {
    const storeValue = {input: '', ...item}
    state.value.push(storeValue)
  })
})

const submitHandler = (e: SubmitEvent) => {
  e.preventDefault()
  emit('submit', state.value)
}

</script>

<template>
  <form @submit="e=> submitHandler(e)">
    <div v-for="(item, i) in state" :key="item?.name">
      <label :for="item?.name">{{ item.label }}</label>
      <input :type="item?.type" v-model="item.input"/>
      <p v-if="errors[i][item.name]">{{ errors[i][item.name] }}</p>
    </div>
    <button type="submit" :disabled="!isValid">Submit</button>
  </form>
</template>

<style scoped>

</style>