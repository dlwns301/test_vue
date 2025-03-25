<!-- App.vue (부모 컴포넌트) -->
<template>
  <ul>
    <TodoItem
      v-for="task in tasks"
      :key="task.id"
      :sangsokData="task"
      @toggle-done="toggleTask"
      @remove-todo="removeTask"
    />
  </ul>
</template>

<script setup>
import TodoItem from './test/TodoItem.vue'
import { ref } from 'vue'

const tasks = ref([
  { id: 1, text: 'Vue 배우기', done: false },
  { id: 2, text: 'Pinia 적용하기', done: false }
])

function toggleTask(id) {
  const task = tasks.value.find((t) => t.id === id)
  if (task) task.done = !task.done
}

function removeTask(id) {
  tasks.value = tasks.value.filter((t) => t.id !== id)
}
</script>