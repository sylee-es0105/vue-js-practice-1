<template>
  <h1>구구단</h1>
  <p>2 ~ 19 숫자 선택</p>
  <select v-model="targetNumber" @change="changeNumber">
    <option value="0">==선택==</option>
    <option v-for="i in 18" :key="i" :value="i+1" v-text="i+1"></option>
  </select>
  <br>
  <label><input type="checkbox" v-model="searchOption" true-value="num" false-value="str" @change="changeNumber">&nbsp;숫자로 검색</label>
  <ul v-if="targetNumber >= 2">
    <li v-for="j in 19">{{ targetNumber }} * {{ j }} = {{ targetNumber * j }}</li>
  </ul>
  <hr>
  <p>포함되는 숫자 표시</p>
  <input v-for="num in showNumbers" :key="num" :value="num">
</template>

<script setup>
 import { ref } from "vue";

 const targetNumber = ref(0);
 const searchOption = ref('str');
 const showNumbers = ref([]); 
 
function changeNumber() {
  showNumbers.value = [];

  if (targetNumber.value == 0) {
    return;
  }

  if (searchOption.value == 'str') {
    for (let i = 1; i <= 19; i++ ) {
      if (i.toString().search(targetNumber.value) != -1) {
        showNumbers.value.push(i);
      }
    }
  } else {
    for (let i = 1; i <= 19; i++) {
      if (i == targetNumber.value) {
        showNumbers.value.push(i);
      }
    }
  }
}
  
</script>

<style scoped>

</style>
