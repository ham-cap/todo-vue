<script>
export default {
  props: {
    todos: Array
  }
};
</script>

<template>
  <ul>
    <li v-for="(todo, index) in this.todos" v-bind:key="index">
      <div class="todo-in-the-list">{{ todo }}</div>
        <button @click="$emit('deleteTodo', index)">Delete</button>
        <button @click="$emit('editTodo', index)">Edit</button>
    </li>
  </ul>
</template>
