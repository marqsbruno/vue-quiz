<script setup>
import { defineProps } from 'vue'
import { RouterLink } from 'vue-router'
RouterLink

const { quizLength, correctAnswers } = defineProps(['correctAnswers', 'quizLength'])
</script>

<template>
  <div class="results">
    <p>Result</p>
    <h1>{{ correctAnswers }}/{{ quizLength }}</h1>
    <RouterLink to="/">Go back</RouterLink>
  </div>
</template>

<style scoped>
.results {
  text-align: center;
  padding: 100px 0;
}

p {
  font-size: 25px;
}

h1 {
  font-size: 80px;
}
</style>
