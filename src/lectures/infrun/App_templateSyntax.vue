<template>
  <div>
    <h2>보간법</h2>
    <p>{{ message }}</p>
    <p v-once>{{ message }}</p>
    <button v-on:click="message = message + '!'">Click!</button>
    <h2>v-html</h2>
    <p>{{ rawHtml }}</p>
    <p v-html="rawHtml"></p>
    <hr />
    <h2>속성 바인딩</h2>
    <div v-bind:title="dynamicTitle">마우스를 올려보세요</div>
    <input type="text" value="이름" v-bind:disabled="isInputDisabled" />
    <input :="attrs" />
    <h2>java-script</h2>
    {{ message.split('').reverse().join('') }}
    {{ isInputDisabled ? '예' : '아니요'}}<br />
</div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup () {
    const message = ref('안녕하세요!');
    const rawHtml = ref('<strong>안녕하세요<strong>');

    const dynamicTitle = ref('진짜로 올렸니..?');
    const isInputDisabled = ref(true);
    const attrs = ref({
      type: 'text',
      value: '12345',
      disabled: false,
    })
    
    return {
      message,
      rawHtml,
      dynamicTitle,
      isInputDisabled,
      attrs,
    }
  }
}
</script>

<style lang="scss" scoped>

</style>