<template>
  <div>
    <md-field>
      <md-input
        v-model="currentTodo"
        @keydown.enter="addTodo()"
        @dblclick="editedTodo()"
        placeholder="Add a todo"
      ></md-input>
    </md-field>
    <ul class="todos">
      <li
        v-for="todo in todos"
        :key="todo.id"
        :class="{ editing: todo == editedTodo }"
      >
        {{ todo.label }}
        <button @click="removeTodo(todo)">Delete</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      todos: [],
      currentTodo: ""
    };
  },
  methods: {
    addTodo() {
      this.todos.push({
        id: this.todos.length,
        label: this.currentTodo,
        completed: false
      });
      this.currentTodo = "";
    },
    removeTodo(todo) {
      var index = this.todos.indexOf(todo);
      this.todos.splice(index, 1);
    },
    editedTodo() {}
  }
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
.editing {
  display: block;
}
body {
  background-color: bisque;
}
</style>
