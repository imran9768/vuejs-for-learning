<template>
  <div class="container">
    <h1>Vue Day 1 – Basic Example</h1>

    <input v-model="name" type="text" placeholder="Enter your name" />

    <p v-if="name">Hello, {{ name }} 👋</p>

    <p v-else>Please enter your name</p>

    <input
      v-model="description"
      type="text"
      placeholder="Enter a description"
    />
    <p v-if="description">Description: {{ description }}</p>
    <p v-else>Please enter a description</p>

    <button @click="clearName">Clear</button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      name: "",
      description: "",
    };
  },
  methods: {
    clearName() {
      this.name = "";
      this.description = "";
    },
  },
};
</script>

<style scoped>
h1 {
    font-size: 25px;
}

.container {
  padding: 20px;
  max-width: 400px;
}

input {
  padding: 8px;
  width: 100%;
  margin-bottom: 10px;
}

button {
  padding: 8px 16px;
  cursor: pointer;
}
</style>
