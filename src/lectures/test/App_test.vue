<template>
  <div>
    <input :value="text" @input="onInput" placeholder="여기에 입력하기">
    <br/>
    <input v-model="text">
    <br/>
    <input placeholder="비밀번호를 입력하세요">
    <button @click="toggle">토글 버튼</button>
    <h1 v-if="awsome" >Vue는 굉장해! 엄청나!</h1>
    <h1 v-else>오 안돼 😢</h1>
    <br/>

    <!-- submit : form이 제출 될때 실행할 이벤트를 설정-->
     <!-- prevent : 기본 동작(새로고침)을 막음-->
    <form @submit.prevent="addTodo"> 
     <input v-model="newTodo" required placeholder="new todo">
     <button>할 일 추가</button>
    </form>
    <ul>
      <li v-for="todo in todos" :key="todo.id">
        {{ todo.text }}
        <button @click="removeTodo(todo)">X</button>
      </li>
    </ul>
  </div>
</template>

<script>
import { watch,ref,computed,reactive } from 'vue';

export default {
  setup () {
    const text = ref('text');
    const awsome = ref(true)

    const onInput = (e) => {
      text.value = e.target.value
      console.log('뭐가 바뀌는지 보자 : ', text.value)
    }

    const toggle= () => {
      awsome.value = !awsome.value
    }

    const showMessage = () => {
      console.log('if문이 실행될때 실행한다 이그야!')
    }

    watch(awsome, (newValue) => {
      if (newValue) {
        showMessage();
      }
    })

    // 각 할 일에 고유한 ID 부여
    let id = 0

    const newTodo = ref('');
    const todos = ref([
      { id: id++, text: 'HTML 배우기' },
      { id: id++, text: 'JavaScript 배우기' },
      { id: id++, text: 'Vue 배우기' }
    ]);

    const addTodo = () => {
      todos.value.push({id: id++, text: newTodo.value});
      newTodo.value = ''
    }

    const removeTodo = (todo) => {
      todos.value = todos.value.filter((t) => t !== todo);
    }

    return {
      text,
      onInput,
      toggle,
      awsome,
      addTodo,
      removeTodo,
      todos,
      newTodo,
    }
  }
}
</script>

<style lang="scss" scoped>

</style>