<template>
  <div>
    <li v-for="item in items" :key="item.id">
      {{ item }}
    </li>
    <!-- 배열 순회 -->
    <p>--------------- 배열 순회---------------------</p>
    <li v-for="(item, index) in items" :key="item.id">
      {{ item }} - {{ index }} - {{ item.id }}
    </li>
    <!-- 객체 순회 -->
    <p>----------------객체 순회---------------------</p>
    <li v-for="(value, key, index ) in gagche" :key="key">
      {{ key }} - {{ value }} - {{ index }}
    </li>
    <p>-------------------------------------</p>
    <button @click="addItem">추가</button>
  </div>
</template>

<script>
import { reactive, ref } from 'vue';

export default {
  setup () {
    const msg = ref('안녕하세요');
    const items = ref([
      { id: 1, message: '메시지1' },
      { id: 2, message: '메시지2' },
      { id: 3, message: '메시지3' },
    ]);

    const gagche = reactive({
      title: '제목입니다.',
      author: '메시지1',
      publishedAt: '2021-08-01',
    });
    
    const addItem = () => {
      items.value.push({ id : Date.now(), message: '새로운 메시지'+items.value.length});
    }

    return {msg, items, addItem, gagche};
  }
}
</script>

<style lang="scss" scoped>

</style>