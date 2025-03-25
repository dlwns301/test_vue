<template>
  <div>
    <p>
      {{ counter }}
    </p>
    <p>
    {{ message }}
    </p>
    <button @click="increment">up click!</button>
    <button @click="decrement">down click!</button>
    <button @click="change">change click!</button>
  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup () {
    const counter = ref(0);
    const message = ref('hello vue3');
    const increment = () => {
      counter.value++;
    }
    const decrement = () => {
      counter.value--;
    }
    const change = () => {
      message.value = '바꿈 ㅎㅎ';
    }
    return {
      counter,
      message,
      increment,
      decrement,
      change,
    };
  }
}
</script>

<style lang="scss" scoped></style>