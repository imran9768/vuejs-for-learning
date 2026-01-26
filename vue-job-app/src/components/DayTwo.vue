<script>
import { ref, reactive, computed, watch } from 'vue'

export default {
  setup() {
    // ref
    const count = ref(0)

    // reactive
    const user = reactive({
      name: '',
      age: ''
    })

    // computed
    const ageStatus = computed(() => {
      return user.age >= 18 ? 'Adult' : 'Minor'
    })

    // watch
    watch(count, (newVal, oldVal) => {
      console.log('Count changed from', oldVal, 'to', newVal)
    })

    watch(
      () => user.age,
      (newAge) => {
        console.log('Age changed:', newAge)
      }
    )

    return {
      count,
      user,
      ageStatus
    }
  }
}
</script>

<template>
  <div class="container">
    <h1>Vue Day 2 – Reactivity</h1>

    <!-- ref example -->
    <h2>Counter (ref)</h2>
    <button @click="count--">-</button>
    <span>{{ count }}</span>
    <button @click="count++">+</button>

    <!-- reactive example -->
    <h2>User Form (reactive)</h2>
    <input v-model="user.name" placeholder="Name" />
    <input v-model="user.age" placeholder="Age" type="number" />

    <p>Name: {{ user.name }}</p>
    <p>Age: {{ user.age }}</p>

    <!-- computed example -->
    <h2>Computed</h2>
    <p>Status: {{ ageStatus }}</p>
  </div>
</template>

<style scoped>
.container {
  padding: 20px;
}
button {
  margin: 5px;
}
input {
  display: block;
  margin: 5px 0;
  padding: 6px;
}
</style>
