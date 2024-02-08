<template>
  <h1>구구단</h1>
  몇 단? : 
  <select v-model="selectedDan">
    <option value="0">==선택==</option>
    <option v-for="danNumber in danNumbers" :key="danNumber" :value="danNumber" v-text="danNumber"></option>
  </select>
  <br>
  결과 검색 : <input type="number" v-model="keyword">
  <br>
  <label><input type="checkbox" v-model="searchOption" true-value="num" false-value="str">&nbsp;숫자로 검색</label>
  <hr style="margin: 15px 0 10px">
  <ul v-show="selectedDan != 0">
    <li v-for="danNumber in danNumbers" :key="danNumber" v-show="isVisible(mul(selectedDan, danNumber))">{{ selectedDan }} * {{ danNumber }} = {{ mul(selectedDan, danNumber) }}</li>
  </ul>
</template>

<script setup>
 import { ref } from "vue";

 const maxDanNumber = 19;
 const selectedDan = ref(0);
 const searchOption = ref('str');
 const danNumbers = ref(Array.from({length: maxDanNumber}, (_, i) => i + 1));
 const keyword = ref('');
  
function mul(number1, number2) {
  return number1 * number2;
}

function isVisible(mulResult) {
  if (keyword.value == '') {
    return true;
  }

  if (searchOption.value == 'str') {
    if (mulResult.toString().search(keyword.value) != -1) {
      return true;
    }
  } else if (searchOption.value == 'num') {
    if (mulResult == keyword.value) {
      return true;
    }
  }

  return false;
}

</script>

<style scoped>

</style>
