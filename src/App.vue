<template>
  <div id="app">
    <todo-header></todo-header>
    <todo-input
            v-on:addToDoList="addTodo"
    ></todo-input>
    <todo-list
            v-bind:propsdata="todoItems"
            @removeTodo="removeTodo"
            @update="updateTodo"
    ></todo-list>
    <todo-footer
           @removeAll="clearAll"
    ></todo-footer>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
  components: {
    'TodoHeader': TodoHeader, // 애플리케이션 이름 표시
    'TodoInput': TodoInput, // 할 일 입력 및 추가
    'TodoList': TodoList, // 할 일 목록 표시 및 특정 할 일 삭제
    'TodoFooter': TodoFooter // 할 일 모두 삭제
  },
  data:()=> ({
      todoItems: [],
      todoList: "",
  }),
  created() {
    if (localStorage.length > 0) {
      console.log(localStorage.length);
      for (let i = 0; i < localStorage.length; i++) {
        this.todoItems.push(localStorage.key(i));
        console.log(this.todoItems);
      }
    }
  },
  methods: {
    addTodo(todoItem) {
      localStorage.setItem(todoItem, todoItem);
      this.todoItems.push(todoItem);
    },
    clearAll() {
      localStorage.clear();
      this.todoItems = [];
    },
    removeTodo(todoItem, index) {
      console.log(todoItem)
      console.log(index)
      localStorage.removeItem(todoItem);
      this.todoItems.splice(index, 1);
    },
    updateTodo(todoItem, index) {
      console.log(todoItem)
      console.log(index)
      this.todoItems[index].concat(todoItem)
     /* localStorage.setItem(this.todoItems[index], this.todoItems[index]);
      this.todoItems[index].push(todoItem);*/
    },
  },
  name: 'App',

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
