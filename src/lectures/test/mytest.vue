<script setup>
import { ref, computed, onMounted } from 'vue'
import '@/assets/style.css'

let id = 0

const newTodo = ref('')
const searchQuery = ref('') // 검색어 저장
const hideCompleted = ref(false)
const todos = ref([])

onMounted(() => {
  const savedTodos = localStorage.getItem('todos')
  if (savedTodos) {
    todos.value = JSON.parse(savedTodos)
    id = todos.value.length ? todos.value[todos.value.length - 1].id + 1 : 0
    console.log('onmaunted : ', todos.value)
  } else {
    todos.value = 
    [{ id: id++, text: 'db_data_01', done: true, isEditing: false, important: false },
    { id: id++, text: 'db_data_02', done: true, isEditing: false, important: false },
    { id: id++, text: 'db_data_03', done: false, isEditing: false, important: false }]
  }
})

// ✅ 검색 및 완료 항목 필터링 적용
const filteredTodos = computed(() => {
  let filtered = hideCompleted.value
    ? todos.value.filter((t) => !t.done)
    : todos.value

  if (searchQuery.value) {
    filtered = filtered.filter((t) =>
      t.text.toLowerCase().includes(searchQuery.value.toLowerCase())
    )
  }

  return filtered
})

function addTodo() {
  todos.value.push({ id: id++, text: newTodo.value, done: false, important: false })
  newTodo.value = ''
}

function removeTodo(todo) {
  // 확인 창 띄우기
  const isConfirmed = confirm('정말 삭제하시겠습니까?');

  if (isConfirmed) {
    todos.value = todos.value.filter((t) => t !== todo);
    console.log('삭제된 todo:', todo);
  } else {
    console.log('삭제 취소');
  }
}

function editTodo(todo) {
  todo.originalText = todo.text
  todo.isEditing = true
}

function saveTodo(todo) {
  todo.isEditing = false
}

function cancelTodo(todo) {
  todo.text = todo.originalText
  todo.isEditing = false
}

function toggleImportant(todo) {
  todo.important = !todo.important
}

function webSave() {
  localStorage.setItem('todos',JSON.stringify(todos.value))
  console.log('save : ', todos.value)
  alert('저장에 성공하였습니다.')
}

const props = defineProps(['foo'])
console.log('props : ', props.foo)

</script>

<template>
  <div class="todo-container">
    
    <!-- ✅ 상단 영역 -->
    <div class="top-bar">
      <h1>Todo List</h1>
      <input v-model="searchQuery" placeholder="검색..." class="search-input">
      <button @click="hideCompleted = !hideCompleted" class="toggle-btn">
        {{ hideCompleted ? 'Show All' : 'Hide Completed' }}
      </button>
    </div>

    <!-- ✅ 입력 폼 -->
    <form @submit.prevent="addTodo" class="todo-form">
      <input v-model="newTodo" required placeholder="새 할 일 추가..." class="todo-input">
      <button class="add-btn">Add</button>
    </form>

    <!-- ✅ 할 일 리스트 -->
    <ul class="todo-list">
      <li v-for="todo in filteredTodos" :key="todo.id" class="todo-item">
        <div class = "left-content">
          <input type="checkbox" v-model="todo.done" class="todo-checkbox">
          
          <form @submit.prevent="saveTodo(todo)">
            <!-- 수정 중이면 input 창 -->
            <input v-if="todo.isEditing" v-model="todo.text" class="edit-input">
            
            <!-- 수정 중이 아닐 때 기존 텍스트 표시 -->
            <span v-else :class="{ done: todo.done, important: todo.important }">{{ todo.text }}</span>  
          </form>
        </div>
        <!-- 버튼들 -->
        <div class="btn-group">
          <button v-if="!todo.isEditing" @click="editTodo(todo)" class="edit-btn">✏️</button>
          <button v-if="!todo.isEditing" @click="toggleImportant(todo)" class="important-btn">⭐️</button>
          <button v-if="todo.isEditing" @click="saveTodo(todo)" class="save-btn">💾</button>
          <button v-if="todo.isEditing" @click="cancelTodo(todo)" class="cancel-btn">❎</button>
          <button v-if="!todo.isEditing" @click="removeTodo(todo)" class="delete-btn">❌</button>
        </div>
      </li>
    </ul>
    <button @click="webSave">저장</button>

  </div>
</template>

