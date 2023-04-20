<script>
export default {
  data () {
    return {
      input: ''
    }
  },
  methods: {
    clearInput: function () {
      this.input = ''
    }
  }
}
</script>

<template>
  <div>
    <input v-model="input" type="text" />
    <button @click="$emit('addTodo', this.input)">Add</button>
  </div>
</template>
