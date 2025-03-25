<template>
  <div>
    <h2>반응형 메시지</h2>
    <p>{{ reactiveMessage }}</p>
    <button v-on:click="addReactiveMessage">add message</button>
    <h2>일반 메시지</h2>
    <p>{{ normalMessage }}</p>
    <button v-on:click="addNormalMessage">add message</button>
  </div>
</template>

<script>
import { isRef, onMounted, onBeforeMount, ref } from 'vue';

export default {
  setup() {
    console.log('setup()');
    const reactiveMessage = ref('reactive message');
    const addReactiveMessage = () => {
      reactiveMessage.value = reactiveMessage.value + '!';
    };
    //console.log('isRef(reactiveMessage): ', isRef(reactiveMessage));

    const normalMessage = 'normal message';
    const addNormalMessage = () => {
      //normalMessage.value = normalMessage.value + '!';
      console.log('일반 변수는 직접 변경할 수 없습니다.');
    };
    //console.log('isRef(normalMessage): ', isRef(normalMessage));
    

    onMounted(()=>{
      console.log('onMounted');
    });

    onBeforeMount(()=>{
      console.log('onBeforeMounted');
    });

    return {
      reactiveMessage,
      normalMessage,
      addReactiveMessage,
      addNormalMessage,
    };
  },
};
</script>

<style></style>
