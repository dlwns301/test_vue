<template>
  <div 
    class="text"
    :class="{active : isActive, 'text-danger' : hasError}"
    >
    텍스트 입니다.
  </div>
  <button @click="toggle">두껍게</button>
  <button @click="hasError = !hasError">파란색</button>
</template>

<script>
import {ref, reactive} from 'vue';

export default {
  setup () {
    const isActive = ref(true)
    const hasError = ref(false)
    
    const toggle = () => {
      isActive.value = !isActive.value
    }

    return {isActive, toggle, hasError}
  }
}
</script>

<style>
.text.active {
  font-weight: 900;
}
.text.text-danger {
  color : blue;
}

</style>