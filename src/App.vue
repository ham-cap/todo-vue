<script>
export default {
  data() {
    return {
      newTodo: "",
      todos: [],
    };
  },
  methods: {
    addTodo: function () {
      if (this.newTodo === "") return;
      this.todos.push(this.newTodo);
      localStorage.setItem("todoList", JSON.stringify(this.todos));
      this.newTodo = "";
    },
  },
};
</script>

<template>
  <div>
    <h1>ToDo</h1>
    <p>{{ $data }}</p>
    <input v-model="newTodo" type="text" />
    <button @click="addTodo">Add</button>
  </div>
</template>
