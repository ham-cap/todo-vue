<script>
import CreateForm from "./components/CreateForm.vue";
import EditForm from "./components/EditForm.vue";
import TodoList from "./components/TodoList.vue";

export default {
  components: {
    CreateForm,
    EditForm,
    TodoList,
  },
  data() {
    return {
      newTodo: "",
      todos: [],
      editing: false,
      selectedTodo: "",
      selectedIndex: "",
      updatedTodo: "",
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
      this.todos.splice(index, 1)
      localStorage.setItem("todoList", JSON.stringify(this.todos));
    },
    editTodo: function (index) {
      this.editing = true;
      const currentTodosJson = localStorage.getItem('todoList');
      const currentTodos = JSON.parse(currentTodosJson);
      this.selectedTodo = currentTodos[index];
      this.selectedIndex = index;
    },
    updateTodo: function (event, index) {
      this.updatedTodo = event;
      if (this.updatedTodo === "") return;
      this.todos.splice(index, 1, this.updatedTodo);
      localStorage.setItem("todoList", JSON.stringify(this.todos));
      this.$refs.editForm.clearChangedTodo();
      this.editing = false;
      this.selectedTodo = "";
      this.selectedIndex = "";
      this.updatedTodo = "";
    }
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
    <CreateForm ref="createForm" v-on:addTodo="addTodo" v-if="this.editing === false" />
    <EditForm ref="editForm" v-on:updateTodo="updateTodo" v-bind:selectedTodo="selectedTodo" v-bind:selectedIndex="selectedIndex" v-else />
    <TodoList v-on:deleteTodo="deleteTodo" v-on:editTodo="editTodo" v-bind:todos="this.todos" />
  </div>
</template>
