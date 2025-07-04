<script setup lang="ts">
const emit = defineEmits<{ (e: 'themeChange'): void }>()

</script>

<template>
  <button @click="emit('themeChange')">
    <slot>Theme Changer</slot>
  </button>
</template>

<style scoped>

</style>