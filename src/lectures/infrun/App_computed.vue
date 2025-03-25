<template>
  <div>
    <h2>{{ teacher.name }}</h2>
    <h3>강의가 있습니까?</h3>
    <!-- <p>{{ teacher.lectures.length > 0 ? '있음' : '없음' }}</p> -->
    <p>{{ hasLecture }}</p>
    <p>{{ existLecture() }}</p>
    <p>바뀐 성 : {{ firstNameChange }}</p>
    <p>fullName : {{ fullName }}</p>
    
  </div>
</template>

<script>
import { ref,computed,reactive } from 'vue';

export default {
  setup () {
    const teacher = reactive({
      name : '짐코딩',
      lectures: ['HTML/CSS', 'JavaScript', 'Vue3'],
    });

    const hasLecture = computed(() => {
      return teacher.lectures.length > 0 ? '있음' : '없음';
    });

    const existLecture = () => {
      return teacher.lectures.length > 0 ? '있음' : '없음'; 
    }

    const counter = ref(0);

    const firstName = ref('홍');
    const lastName = ref('길동');

    const firstNameChange = computed(() => {
      console.log('firstNameChange start');
      return firstName.value = '최';
    })

    const fullName = computed({
      get() {
        return firstName.value + ' ' + lastName.value;
      },
      set(value){
        console.log('value ', value);
        console.log(value.split(' '));
        [firstName.value, lastName.value] = value.split(' ');
      },
    });
    console.log('console 출력: ', fullName.value);
    fullName.value = '짐 코딩';
    fullName.value = '이 준호';

    return {
      teacher,
      hasLecture,
      existLecture,
      fullName,
      firstNameChange,
    }
  }
}
</script>

<style lang="scss" scoped>

</style>