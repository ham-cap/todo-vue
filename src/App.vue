<script>
import CreateForm from "./components/CreateForm.vue";

export default {
  components: {
    CreateForm,
  },
  data() {
    return {
      newTodo: "",
      todos: [],
    };
  },
  methods: {
    addTodo: function (event) {
      this.newTodo = event;
      if (this.newTodo === "") return;
      this.todos.push(this.newTodo);
      localStorage.setItem("todoList", JSON.stringify(this.todos));
      this.newTodo = "";
      this.$refs.createForm.clearInput();
    },
    deleteTodo: function (index) {
      this.todos.splice(index, 1);
    },
  },
  mounted() {
    if (Object.prototype.hasOwnProperty.call(localStorage, "todoList")) {
      const todoListJson = localStorage.getItem("todoList");
      this.todos = JSON.parse(todoListJson);
    } else {
      localStorage.setItem("todoList", this.todos);
    }
  },
};
</script>

<template>
  <div>
    <h1>ToDo</h1>
    <p>Appのデータ{{ $data }}</p>
    <CreateForm ref="createForm" v-on:addTodo="addTodo" />
    <ul>
      <li v-for="(todo, index) in todos" v-bind:key="index">
        {{ index }}：{{ todo }}
        <button v-on:click="deleteTodo(index)">Delete</button>
        <button v-on:click="editTodo(index)">Edit</button>
      </li>
    </ul>
  </div>
</template>
