<template>
  <div class="box">
    <h1>Day 5 – Composition API</h1>

    <button @click="decrement">-</button>
    <span>{{ count }}</span>
    <button @click="increment">+</button>

    <p>Status: {{ status }}</p>
  </div>
</template>

<script>
import { ref, computed, onMounted, onUnmounted } from 'vue'

export default {
  setup() {
    const count = ref(0)

    const increment = () => count.value++
    const decrement = () => count.value-- 

    const status = computed(() =>
      count.value >= 5 ? 'High' : 'Low'
    )

    onMounted(() => {
      console.log('Component Mounted')
    })

    onUnmounted(() => {
      console.log('Component Unmounted')
    })

    return {
      count,
      increment,
      decrement,
      status
    }
  }
}
</script>

<style scoped>
.box { padding: 20px; }
button { margin: 5px; }
</style>
