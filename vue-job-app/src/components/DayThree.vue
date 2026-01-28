<template>
  <div class="container">
    <h1>Vue Day 3 – Todo App</h1>

    <!-- Add Todo -->
    <div class="add-todo">
      <input
        v-model="newTodo"
        placeholder="Enter new todo"
        @keyup.enter="addTodo"
      />
      <button @click="addTodo">Add</button>
    </div>

    <!-- Conditional Rendering -->
    <p v-if="todos.length === 0">
      No todos available 😴
    </p>

    <!-- Todo List -->
    <ul v-else>
      <li
        v-for="(todo, index) in todos"
        :key="todo.id"
      >
        <span :class="{ done: todo.completed }">
          {{ index + 1 }}. {{ todo.text }}
        </span>

        <button @click="toggleTodo(todo.id)">
          {{ todo.completed ? 'Undo' : 'Done' }}
        </button>

        <button @click="removeTodo(todo.id)">
          ❌
        </button>
      </li>
    </ul>
  </div>
</template>

<script>
import { ref } from 'vue'

export default {
  setup() {
    const newTodo = ref('')
    const todos = ref([])

    const addTodo = () => {
      if (!newTodo.value.trim()) return

      todos.value.push({
        id: Date.now(),
        text: newTodo.value,
        completed: false
      })

      newTodo.value = ''
    }

    const toggleTodo = (id) => {
      const todo = todos.value.find(t => t.id === id)
      todo.completed = !todo.completed
    }

    const removeTodo = (id) => {
      todos.value = todos.value.filter(t => t.id !== id)
    }

    return {
      newTodo,
      todos,
      addTodo,
      toggleTodo,
      removeTodo
    }
  }
}
</script>

<style scoped>
.container {
  max-width: 500px;
  padding: 20px;
}

.add-todo {
  display: flex;
  gap: 10px;
}

ul {
  padding: 0;
}

li {
  list-style: none;
  margin: 8px 0;
  display: flex;
  align-items: center;
  gap: 10px;
}

.done {
  text-decoration: line-through;
  color: gray;
}
</style>
