<template>
  <!-- <input type="text" v-bind:value="message">
  <p>{{ message }}</p> -->
  <input type="text" v-model="message">
  <p>{{ message }}</p>

  <!-- 반복문 -->
  <ul>
    <!-- filter로 걸러낼 수 있다-->
      <!-- <li v-for="(item, index) in items.filter((i)=>i.x % 2 ==0)" :key="index">x({{ item.x }}) * y({{ item.y }}) = {{ item.x * item.y }}</li> -->

      <li v-for="(item, index) in items" :key="index">x({{ item.x }}) * y({{ item.y }}) = {{ item.x * item.y }}</li>
  </ul>

  <Select>
    <option v-for="item in items" :key="item.x" :value="item.y" >{{ item.x % 2 == 0 ? item.x : 'none' }}</option>
  </Select>
  <br><br>
  x : <input type="number" v-model="xNew">{{ xNew }}<br>
  y : <input type="number" v-model="yNew">{{ yNew }}<br>

  <!-- <button type="button" v-on:click="">추가</button> -->
  <!-- v-on:은 @로 축약 가능 -->
  <!-- () 넣어도 되고 안넣어도 됨 -->
  <!-- addItem은 addItem($event)와 동일하다 -->
  <!--  :: 일급함수 -> $event에 대한 첫 번째 값을 넣어서 보낸다 -->
  <!-- 스와이프 : 첫 위치 저장, 스와이프 하는 동안 이벤트가 계속 발생하는 것 -->
  <!-- 우클릭 시 브라우저의 기본 메뉴가 아니라, 중간에 가로채서 커스텀 메뉴가 보이게 할 수도 있고 그렇다 -->
  <button type="button" @click="addItem">추가</button><br><hr>
  </template>
  
  <script setup>
   import { ref } from "vue";
    // 값을 먼저 잡아 놓고 화면을 그린다.

  // 1. 메시지를 인풋박스에 넣으면
  // 2. 아래 p 태그에 같은 값을 넣는다

  // 단방향 바인딩
  // 값이 바뀌지 않는다면 const로 해서 v-bind:value="message" 해도 됨
  // -> v-bind 생략하고 :value="message" 가능
  // 
  // const message = '13242342';

  const message = ref("ddfsfsdfsd");
  // const로 정의하면 test 자체를 바꿀 수는 없지만 test.abcd의 값은 바꿀 수 있다
  const test = {abcd: 2323};
  test.abcd = '2342323423';

  message.value = '23423423423';

  // 전역변수로 보내기
  // globalThis.message = message;
  
  // 반복문
  // ref로 선언된 애들은 무조건 .value 붙여줘야 쓸 수 있다
  const items = ref([ {x: 100, y: 20}, {x: 50, y: 40}, {x: 9, y: 11}]);

  const xNew = ref();
  const yNew = ref();

  function addItem() {
    items.value.push({ x: xNew.value, y: yNew.value});
  }

    
  </script>
  
  <style scoped>
  
  </style>
  