<template>
  <div id="app">
    <header>
      <h1>TODO it!</h1>
    </header>
    <TodoInput @addTodo="addTodo"></TodoInput>
    <TodoList :propsData="todoList" @removeTodo="removeTodo"></TodoList>
    <TodoFooter @removeAll="clearAll"></TodoFooter>
  </div>
</template>

<script>
import TodoList from './components/TodoList.vue';
import TodoInput from './components/TodoInput.vue';
import TodoFooter from './components/TodoFooter.vue';

export default {
  name: 'App',
  data() {
    return {
      todoList: [],
    }
  },
  methods: {
    addTodo(todoItem) {
      localStorage.setItem(todoItem, todoItem);
      this.todoList.push(todoItem);
    },
    clearAll() {
      localStorage.clear();
      this.todoList = [];
    },
    removeTodo(todoItem, index) {
      localStorage.removeItem(todoItem);
      this.todoList.splice(index, 1);
    }
  },
/*     created() { // data, component 인지 후 실행
      if (localStorage.length > 0) {
        for (let i = 0; i < localStorage.length; i++) {
          this.todoList.push(localStorage.key[i]);
        }
      }
    }, */
  //mounted() { data, component 출력 후 최종 작업}
  components: {
    TodoList,
    TodoInput,
    TodoFooter,
  }
}
</script>

<style>
body{
  background: #f4f4f4;
}
#app {
  text-align: center;
  padding: 0 100px;
}

h1 {
  color: #008080;
  margin: 50px 0;
}
button {
  cursor: pointer;
}
</style>
