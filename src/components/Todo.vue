<template>
  <div id="todo">
    <div class="todo-item" @click="toggleComplete" :class="classes">{{ task }}</div>
  </div>
</template>


<script>
export default {
  name: "Todo",
  props: ["todo"],
  data() {
    return {
      isCompleted: this.todo.completed,
      checked: "✅",
      unchecked: "⬜",
    };
  },
  computed: {
    classes: function () {
      return {
        completed: this.isCompleted,
        uncompleted: !this.isCompleted,
      };
    },
    task: function () {
      return this.isCompleted
        ? `${this.checked}  ${this.todo.title}`
        : `${this.unchecked}  ${this.todo.title}`;
    },
  },
  methods: {
    toggleComplete() {
      this.isCompleted = !this.isCompleted;
    },
  },
};
</script>


<style scoped>
* {
  outline: none;
}
.todo-item {
  width: 510px;
  height: 40px;
  line-height: 40px;
  user-select: none;
  padding: 5px 20px;
  text-align: left;
  border-radius: 5px;
  margin: 10px auto;
  border: 2px solid #2a2a2a;
}

.completed {
  color: #a3a3a3;
}

.uncompleted {
  color: #000;
}
</style>
