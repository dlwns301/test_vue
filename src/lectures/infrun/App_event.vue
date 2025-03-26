<template>
  <div>
    <button @click="printEventInfo">printEventInfo</button>
    <button @click="printEventInfo2('hello world', $event)">
      inline event handler
    </button>
    <input @keyup="onKeyHandler" />
    <!-- 알트 + 엔터 -->
    <input @keyup.alt.enter="clear" />
    <p @keyup.alt.enter="clear">?</p>
    <!-- 컨트롤 + 엔터 -->
    <input @keyup.ctrl.enter="send" />

  </div>
</template>

<script>
export default {
  setup () {
  const printEventInfo = event => {
    console.log("event target : ", event.target);
    console.log("tag Name : " , event.target.tagName);
};

  const printEventInfo2 = (messsage, event) => {
    console.log('messsage: ', messsage);
    console.log(event.target);
    console.log(event.target.tagName);
};
  const onKeyHandler = (event) => {
    console.log('event.key: ', event.key);
  }

  const clear = (event) => {
    event.target.value = '타겟은! 타겟이다..'; // 입력 필드 비우기
};

    return {printEventInfo, printEventInfo2, clear, onKeyHandler}
  }
}
</script>

<style lang="scss" scoped>

</style>