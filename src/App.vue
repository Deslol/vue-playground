<script setup>

import DynamicListFilter from "@/components/DynamicListFilter.vue";
import ReusableBtn from "@/components/ReusableBtn.vue";
</script>

<template>
  <v-card>
    <!--    <DynamicListFilter/>-->
    <ReusableBtn label='test' @clicked="console.log('CLICKED')">testing123</ReusableBtn>
  </v-card>
</template>

<style scoped>

</style>
