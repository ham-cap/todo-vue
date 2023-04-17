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
  props: ["selectedTodo", "selectedIndex"]
};
</script>

<template>
  <div>
    <input v-model="changedTodo" type="text" />
    <button @click="$emit('updateTodo', this.changedTodo, this.selectedIndex)">Update</button>
    <p>selectedTodo: {{ selectedTodo }}</p>
    <p>selectedIndex: {{ selectedIndex }}</p>
    <p>EditFormのデータ: {{ $data }}</p>
  </div>
</template>
