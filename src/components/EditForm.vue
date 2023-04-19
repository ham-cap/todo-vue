<script>
export default {
  data() {
    return {
      updatingTodo: this.selectedTodo,
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
    <input v-model="updatingTodo" type="text" />
    <button @click="$emit('updateTodo', this.updatingTodo, this.selectedIndex)">Update</button>
  </div>
</template>
