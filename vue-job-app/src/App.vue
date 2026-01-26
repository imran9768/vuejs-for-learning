<template>
  <div class="container">
    <h1>Vue Job App</h1>
    <DayOne />
    <hr/>
    <DayTwo />
  </div>
</template>

<script>
import DayOne from './components/DayOne.vue';
import DayTwo from './components/DayTwo.vue';

export default {
  components: {
    DayOne,
    DayTwo
  },
};
</script>

<style scoped>
.container {
  padding: 20px;
  max-width: 400px;
}
</style>
