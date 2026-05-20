<template>
  <div class="wrapper">
    <h1>Task manager</h1>

    <div class="input-row">
      <input type="text" placeholder="Add task here" v-model="newTask" />
      <button @click="addTask">Add task</button>
    </div>

    <ul class="task-list">
      <li v-for="task in tasks" :key="task.id" :class="{ done: task.completed }">
        <button class="delete" @click="removeTask(task.id)">X</button>
        <input type="checkbox" v-model="task.completed" />
        <span>{{ task.text }}</span>
      </li>

    </ul>
  </div>
</template>

<script setup>
import { ref } from 'vue'

const newTask = ref("")
const tasks = ref([])

const addTask = () => {
  const text = newTask.value.trim()
  if (!text) {
    return
  }

  tasks.value.push({
    id: Date.now(),
    text: text,
    completed: false,
    favorite: false,
  })

  newTask.value = '';
}

function removeTask(id) {
  tasks.value = tasks.value.filter((t) => t.id !== id)
}

</script>

<style scoped>
.app {
  max-width: 500px;
  margin: 2rem auto;
  font-family: sans-serif;
  text-align: center;
}

.input-row {
  display: flex;
  gap: 0.5rem;
  margin-bottom: 1rem;
}

input {
  flex-grow: 1;
  padding: 0.5rem;
  border-radius: 6px;
  border: 1px solid #ccc;
}

button {
  padding: 0.5rem 1rem;
  border-radius: 6px;
  border: 1px solid #ccc;
  cursor: pointer;
}

.task-list {
  list-style: none;
  padding: 0;
}

.task-list li {
  display: flex;
  align-items: center;
  gap: 0.5rem;
  padding: 0.5rem;
  border-bottom: 1px solid #eee;
}

.task-list li.done span {
  text-decoration: line-through;
  opacity: 0.6;
}
</style>
