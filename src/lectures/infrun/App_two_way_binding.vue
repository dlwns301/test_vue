<template>
  <div>
    <h2>input value</h2>
    <input type="text" v-model.lazy="inputValue" />
    <!-- <input :value="inputValue" 
      @input="event => {inputValue = event.target.value}" /> -->
    <p>{{ inputValue }}</p>


    <h2>textarea value</h2>
    <!-- <textarea :value="textareaValue" 
      @input = "event => {textareaValue = event.target.value}"></textarea> -->
    <textarea v-model="textareaValue"></textarea>
    <div>{{ textareaValue }}</div>

    <h2>checkbox value</h2>
    <label for="checkbox">{{ checkboxValue }}</label>
    <input 
      type="checkbox" 
      id="checkbox" 
      v-model="checkboxValue" 
      true-value="yes"
      false-value="no"
      />
    <!-- <input type="checkbox" :checked = "checkboxValue" @change="event => {checkboxValue = event.target.checked}" /> -->
    <div>{{ checkboxValue }}</div>

    <h3>checkbox value</h3>
    <label>
      <input type="checkbox" v-model="checkboxValues" value="html" />
      HTML
    </label>
    <label>
      <input type="checkbox" v-model="checkboxValues" value="css" />
      CSS
    </label>
    <label>
      <input type="checkbox" v-model="checkboxValues" value="javascript" />
      JAVASCRIPT
    </label>
    <div>{{ checkboxValues }}</div>

    <h2>radio value</h2>
    <label>
      <input type="radio" name="type" value="O" 
      v-model="radioValue"/>
      <!-- :checked = "radioValue === 'O'" 
      @change = "event => {radioValue = event.target.value}" -->
      O형
    </label>
    <label>
      <input type="radio" name="type" value="A" 
      v-model="radioValue"/>
      <!-- :checked = "radioValue === 'A'" 
      @change = "event => {radioValue = event.target.value}" -->
      A형
    </label>
    <div>{{ radioValue }}</div>

    <h2>select value</h2>
    <!-- :value = "selectValue" @change = "event => {selectValue = event.target.value}" -->
    <select v-model="selectValue">
      <option value="html">html 수업</option>
      <option value="css">css 수업</option>
      <option value="javascript">javascript 수업</option>
    </select>
    <div>{{ selectValue }}</div>

  </div>
</template>

<script>
import { ref } from 'vue';

export default {
  setup () {
    const inputValue = ref('');
    const textareaValue = ref('');
    const checkboxValue = ref('yes');
    const radioValue = ref('A');
    const selectValue = ref('css');
    const checkboxValues = ref([]);

    return {inputValue,textareaValue,checkboxValue,radioValue,selectValue,checkboxValues}
  }
}
</script>

<style lang="scss" scoped>

</style>