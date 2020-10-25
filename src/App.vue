<template>
  <div id="app">
    <TodoHeader></TodoHeader>
    <TodoInput></TodoInput>
    <TodoList></TodoList>
    <TodoFooter></TodoFooter>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  name: 'App',
  components: {
    'TodoHeader': TodoHeader, // 애플리케이션 이름 표시
    'TodoInput': TodoInput, // 할 일 입력 및 추가
    'TodoList': TodoList, // 할 일 목록 표시 및 특정 할 일 삭제
    'TodoFooter': TodoFooter // 할 일 모두 삭제
  }
}
</script>

<style>
  body {
    text-align: center;
    background-color: #F6f6f8;
  }
  input {
    border-style: groove;
    width: 200px;
  }
  button {
    border-style: groove;
  }
  .shadow {
    box-shadow: 5px 10px 10px rgba(0, 0, 0, 0.03);
  }
</style>
