<script setup lang="ts">
const props = defineProps({
  label: {
    type: String,
    required: true
  },
  type: {
    type: String,
    default: 'button'
  },
  disabled: {
    type: Boolean,
    default: false
  }
})

const emit = defineEmits(['clicked'])

function onClickHandler() {
  if (props.disabled) return
  emit('clicked')
}
</script>

<template>
  <button @click="onClickHandler" :disabled="disabled">
    <slot>{{ label ?? 'Reusable Button' }}</slot>
  </button>
</template>

<style scoped>

</style>