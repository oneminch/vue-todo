<template>
  <div id="todos">
    <Todo v-for="todo in todos" :todo="todo" :key="todo.id"></Todo>
  </div>
</template>


<script>
import Todo from "./Todo.vue";

export default {
  name: "Todos",
  props: ["todos"],
  components: {
    Todo,
  },
  data() {
    return {
      todoItems: this.todos,
    };
  },
};
</script>


<style scoped>
* {
  outline: none;
}

div {
  margin: 20px auto;
}
</style>
