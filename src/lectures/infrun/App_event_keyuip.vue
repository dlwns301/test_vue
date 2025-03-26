<template>
  <div>
    <input type="text" @keyup.enter="addTodo" />
    <ul>
      <li v-for="(todo, index) in todos" :key="index">
        {{ todo }}
      </li>
    </ul>
  </div>
</template>

<script>
import { reactive, ref } from 'vue';

export default {
  setup () {
    const todos = reactive([]);

    const addTodo = event => {
      console.log('event.key', event.key);
      //if (event.key === 'Enter') { == @keyup.enter
      todos.push(event.target.value);
      event.target.value = '';
      //event.target.focus();
      //}
    }

    return {todos,addTodo}
  }
}
</script>

<style lang="scss" scoped>

</style>