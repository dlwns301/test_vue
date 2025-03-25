<!-- 자식 컴포넌트 -->
<template>
  <li>
    <input type="checkbox" :checked="sangsokData.done" @change="toggleTodo"/>
    {{ sangsokData.text }}
    <button @click="removeTodo">삭제🦊</button>
    <p></p>
  </li>
</template>

<script setup>
const props = defineProps({
  sangsokData: Object, // 부모에서 받은 데이터
  data: Object
})

const emit = defineEmits(['toggle-done', 'remove-todo'])

function toggleTodo() {
  emit('toggle-done', props.sangsokData.id) // 체크 상태 변경 이벤트 전달
}

function removeTodo() {
  emit('remove-todo', props.sangsokData.id) // 삭제 이벤트 전달
}

</script>