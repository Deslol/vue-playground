<script setup lang="ts">

import {onBeforeUnmount, Ref, ref} from "vue";

const props = withDefaults(defineProps<{
  debounceMs?: number
}>(), {
  debounceMs: 300
})

const queryString: Ref<string> = ref('')

const emit = defineEmits<{ (e: 'input', value: string): void }>()

let timeOut: ReturnType<typeof setTimeout> | null = null;

const typingHandler = (e) => {
  clearTimeout(timeOut)
  queryString.value = e.target.value
  timeOut = setTimeout(() => {
    emit('input', queryString.value)
  }, props.debounceMs)
}

onBeforeUnmount(() => {
  clearTimeout(timeOut)
})
</script>

<template>
  <input type="text" @input="e=> typingHandler(e)" :value="queryString"/>
</template>

<style scoped>

</style>