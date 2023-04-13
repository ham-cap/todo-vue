<script>
export default {
  data() {
    return {
      newTodo: "",
    };
  },
  methods: {
    clear: function (){
      console.log('clear')
    },
//     addTodo: function () {
//       if (this.newTodo === "") return;
//       this.todos.push(this.newTodo);
//       localStorage.setItem("todoList", JSON.stringify(this.todos));
//       this.newTodo = "";
//     },
  },
};
</script>

<template>
  <div>
    <p>CreateFormのデータ{{ $data }}</p>
    <input v-model="newTodo" type="text" />
    <button @click="$emit('addTodo', this.newTodo)">Add</button>
  </div>
</template>
