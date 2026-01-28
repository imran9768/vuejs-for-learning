<template>
  <ul>
    <li v-for="todo in todos" :key="todo.id">
      <span :class="{ done: todo.completed }">
        {{ todo.text }}
      </span>

      <button @click="$emit('toggle', todo.id)">
        {{ todo.completed ? 'Undo' : 'Done' }}
      </button>

      <button @click="$emit('remove', todo.id)">
        ❌
      </button>
    </li>
  </ul>
</template>

<script>
export default {
  props: {
    todos: {
      type: Array,
      required: true
    }
  }
}
</script>

<style scoped>
li {
  list-style: none;
  margin: 6px 0;
}
.done {
  text-decoration: line-through;
}
</style>
