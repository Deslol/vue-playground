<script setup>

import DynamicListFilter from "@/components/DynamicListFilter.vue";
import ReusableBtn from "@/components/ReusableBtn.vue";
import SignUpForm from "@/components/SignUpForm.vue";

const submitHandler = (data) => {
  console.log(data)
}
</script>

<template>
  <v-card>
    <!--    <DynamicListFilter/>-->
    <!--    <ReusableBtn label='test' @clicked="console.log('CLICKED')">testing123</ReusableBtn>-->
    <SignUpForm @submit="(e)=> submitHandler(e)"/>
  </v-card>

</template>

<style scoped>

</style>
