<template>
  <div>
    <div :style="styleObject">
      Lorem ipsum dolor sit amet consectetur adipisicing elit. Libero sunt repellendus ratione asperiores doloremque rem magni quos ea expedita eveniet blanditiis labore enim consectetur modi ad, architecto dolores et vel.
    </div>
    <button @click="fontSize++"> + </button>
    <button @click="fontSize--"> - </button>
  </div>
</template>

<script>
import { computed, reactive, ref } from 'vue';

export default {
  setup () {
    // const styleObject = reactive({
    //   color: 'red',
    //   fontSize: '13px',
    // });

    const fontSize = ref('13');

    const styleObject = computed(() =>{
      return {
        color: 'red',
        fontSize: fontSize.value + 'px',
      }
      
    })

    return {styleObject, fontSize}
  }
}
</script>

<style lang="scss" scoped>

</style>