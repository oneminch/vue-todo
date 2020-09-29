<template>
  <div id="addTodo">
    <div class="container">
      <input ref="todoInput" @keyup.enter="addTodo" type="text" required />
      <input @click="addTodo" type="submit" value="Add" />
    </div>
  </div>
</template>


<script>
export default {
  name: "Add",
  props: ["todos"],
  methods: {
    addTodo: function () {
      // console.log();
      if (!this.$refs.todoInput.value) {
        return;
      }
      let todo = {};
      todo.id = this.todos.length;
      todo.title = this.$refs.todoInput.value;
      todo.completed = false;
      this.$emit("add-todo", todo);
    },
  },
};
</script>


<style scoped>
@import url("https://unpkg.com/mvp.css");

.container {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 25px;
}

input {
  margin: 0 10px;
  cursor: pointer;
}

input:first-child {
  width: 400px;
}

input:last-child {
  width: 100px;
}
</style>
