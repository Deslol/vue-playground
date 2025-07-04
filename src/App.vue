<script setup>

import DynamicListFilter from "@/components/DynamicListFilter.vue";
import ReusableBtn from "@/components/ReusableBtn.vue";
import SignUpForm from "@/components/SignUpForm.vue";
import ThemeChanger from "@/components/ThemeChanger.vue";
import {onMounted, onUnmounted, ref, watch} from "vue";
import DebouncedSearchInput from "@/components/DebouncedSearchInput.vue";

// const submitHandler = (data) => {
//   console.log(data)
// }

const darkMode = ref(false)
//
// const themeChangeHandler = () => {
//   darkMode.value = !darkMode.value
//   localStorage.setItem('darkMode', darkMode.value)
// }
//
// onMounted(() => {
//   darkMode.value = localStorage.getItem('darkMode') === 'true'
// })

const dInput = ref('')
</script>

<template>
  <div :style="{
    backgroundColor: darkMode ? 'black' : 'white',
    color: darkMode ? 'white' : 'black',
  }"
       class="container"
  >
    <!--    <DynamicListFilter/>-->
    <!--    <ReusableBtn label='test' @clicked="console.log('CLICKED')">testing123</ReusableBtn>-->
    <!--    <SignUpForm @submit="(e)=> submitHandler(e)"/>-->
    <!--    <ThemeChanger @theme-change="themeChangeHandler">TEST</ThemeChanger>-->
    <DebouncedSearchInput :debounceMs="5000" @input="value => dInput = value"/>
    <p>userInput: {{ dInput }}</p>
  </div>

</template>

<style scoped>
.container {
  height: 100vh;
  width: 100vw;
  display: flex;
  align-content: center;
  justify-content: center;
}
</style>
