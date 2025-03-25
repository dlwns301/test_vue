<template>
  <div>
    <button @click="increment">Click {{ state.count }}</button><br/>
    <button @click="decrement">Click {{ state.deep.count }}</button><br/>
    <button @click="summary">Click {{ sum }}</button>
    <p>{{sum.sum}}</p>
  </div>
</template>

<script>
import { computed, reactive, ref } from 'vue';

export default {
  setup () {
    const state = reactive({
      count:0,
      deep: {
        count:0,
      }
    });
    const increment = () => {
      state.count++;
    }
    function decrement(){
      state.deep.count ++;
    }

    const sum = ref(0);

    const summary = () => {
      sum.value = state.count + state.deep.count;
    }
    return {
      state,
      increment,
      decrement,
      sum,
      summary,
    }
  }
}
</script>

<style lang="scss" scoped>

</style>