<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <h1>A Vue.js Todo App</h1>
    <Add :todos="todos" @add-todo="addNewTodo" />
    <Todos :todos="todos"></Todos>
  </div>
</template>

<script>
import Add from "./components/Add.vue";
import Todos from "./components/Todos.vue";

export default {
  name: "App",
  components: {
    Add,
    Todos,
  },
  data() {
    return {
      todos: [],
    };
  },
  methods: {
    addNewTodo(event) {
      let todoItem = {};
      todoItem = event;
      this.todos.push(todoItem);
      console.log(this.todos);
    },
  },
  created: function () {
    fetch("https://jsonplaceholder.typicode.com/todos?_limit=5")
      .then((response) => response.json())
      .then((json) => {
        this.todos = [...json];
      });
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
img {
  width: 100px;
}
</style>
