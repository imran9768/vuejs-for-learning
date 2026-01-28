<template>
  <div class="todo-input">
    <input
      v-model="text"
      placeholder="Enter todo"
      @keyup.enter="submitTodo"
    />
    <button @click="submitTodo">Add</button>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  emits: ['add-todo'],
  setup(props, { emit }) {
    const text = ref('')

    const submitTodo = () => {
      if (!text.value.trim()) return
      emit('add-todo', text.value)
      text.value = ''
    }

    return {
      text,
      submitTodo
    }
  }
}
</script>

<style scoped>
.todo-input {
  display: flex;
  gap: 10px;
}
</style>
