<template>
  <h1>Counter is: {{ counter }}</h1>
  <button @click="increment">Increment</button>
  <button @click="decrement">Decrement</button>
</template>

<style scoped></style>

<script setup>
import { ref } from "vue"

const counter = ref(0)

function decrement() {
  counter.value--
}

function increment() {
  counter.value++
}
</script>
