<template>
  <div class="wrapper">
    <h1>Task manager</h1>

    <div class="input-row">
      <input type="text" placeholder="Add task here" v-model="newTask"/>
      <button>Add task</button>
    </div>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const newTask = ref("")
const tasks = ref([''])

function addTask() {
  const text = newTask.value.trim()
  if(!text){
    return
  }
  task.value.push()
} 

</script>

<style scoped>
.app {
  max-width: 500px;
  margin: 2rem auto;
  font-family: sans-serif;
  text-align: center;

}
</style>
