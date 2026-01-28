<template>
  <div class="container">
    <h1>Vue Job App</h1>
    <DayOne />
    <hr />
    <DayTwo />
    <hr />
    <DayThree />
    <hr />
    <TodoInput @add-todo="addTodo" />
    <br />
    <DayFour />
    <TodoList :todos="todos" @toggle="toggleTodo" @remove="removeTodo" />
  </div>
</template>

<script>
import { ref } from 'vue'
import DayOne from "./components/DayOne.vue";
import DayTwo from "./components/DayTwo.vue";
import DayThree from "./components/DayThree.vue";
import TodoInput from "./components/TodoInput.vue";
import TodoList from "./components/TodoList.vue";
import DayFour from "./components/DayFour.vue";

export default {
  components: {
    DayOne,
    DayTwo,
    DayThree,
    TodoInput,
    TodoList,
    DayFour
  },
    setup() {
    const todos = ref([])

    const addTodo = (text) => {
      todos.value.push({
        id: Date.now(),
        text,
        completed: false
      })
    }

    const toggleTodo = (id) => {
      const todo = todos.value.find(t => t.id === id)
      todo.completed = !todo.completed
    }

    const removeTodo = (id) => {
      todos.value = todos.value.filter(t => t.id !== id)
    }

    return {
      todos,
      addTodo,
      toggleTodo,
      removeTodo
    }
  }
};
</script>

<style scoped>
.container {
  padding: 20px;
  max-width: 400px;
}
</style>
