<script setup lang="ts">

import {Ref, ref} from "vue";

const props = withDefaults(defineProps<{
  debounceMs?: number
}>(), {
  debounceMs: 300
})

const queryString: Ref<string> = ref('')

const emit = defineEmits<{ (e: 'input', value: string): void }>()

let timeOut: number;

const typingHandler = (e) => {
  clearTimeout(timeOut)
  timeOut = setTimeout(() => {
    queryString.value = e.target.value
    emit('input', queryString.value)
  }, props.debounceMs)
}
</script>

<template>
  <input type="text" @keyup="e=> typingHandler(e)" :value="queryString"/>
</template>

<style scoped>

</style>