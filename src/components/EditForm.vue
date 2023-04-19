<script>
export default {
  data() {
    return {
      changedTodo: this.selectedTodo,
    };
  },
  methods: {
    clearChangedTodo: function() {
      this.changedTodo = "";
    }
  },
  props: {
    selectedTodo: String,
    selectedIndex: Number
  }
};
</script>

<template>
  <div>
    <input v-model="changedTodo" type="text" />
    <button @click="$emit('updateTodo', this.changedTodo, this.selectedIndex)">Update</button>
  </div>
</template>
