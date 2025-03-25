<template>
  <div>
    <p>{{ message1 }}</p>
    <button v-on:click = "change">click</button>
  </div>
</template>

<script>
import { reactive, ref } from 'vue';
export default {
  setup () {
    let message = reactive({
      value : 'Hello Vue!'
    }); //
    let message1 = ref('Hello Vue!');

    const change = () => {
      message1.value = message1.value + '!';
    };

    return {
      message,
      change,
      message1,

    };
  },
};
</script>

<style lang="scss" scoped>

</style>