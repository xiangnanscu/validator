<script setup>
import { ref } from 'vue'
import Validator from '../validator.mjs'

defineProps({
  msg: String
})

const inputValue = ref('511523199901010011')
const errorMsg = ref('')
function validate(v) {
  try {
    Validator.sfzh(inputValue)
    errorMsg.value = ""
  } catch (error) {
    errorMsg.value = error.message
  }
}
</script>

<template>
  <h1>{{ msg }}</h1>
  <input :value="inputValue" @input="inputValue=$event.target.value" />
  <button type="button" @click="validate">validate</button>
  <span v-if="errorMsg">error: {{ errorMsg }}</span>
</template>

<style scoped>
a {
  color: #42b983;
}
</style>
