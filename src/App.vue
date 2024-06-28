<script setup>
import { ref } from 'vue'
import q from './data/quizzes.json'

const quizzes = ref(q)
</script>

<template>
  <div class="container">
    <header>
      <h1>Quizzes</h1>
      <input type="text" placeholder="Search..." />
    </header>
    <div class="options-container">
      <div v-for="quiz in quizzes" :key="quiz.id" class="card">
        <img v-bind:src="quiz.img" alt="" />
        <div class="card-text">
          <h2>{{ quiz.name }}</h2>
          <p>{{ quiz.questions.length }} questions</p>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
.container {
  max-width: 1000px;
  margin: 0 auto;
}

header {
  border: 1px solid black;
  margin-bottom: 10px;
  margin-top: 30px;
  display: flex;
  align-items: center;
  justify-content: center;
}

header h1 {
  font-weight: bold;
  margin-right: 30px;
}

header input {
  border: none;
  background-color: rgba(128, 128, 128, 0.2);
  padding: 7px;
  border-radius: 5px;
}

.options-container {
  display: flex;
  flex-wrap: wrap;
  margin-top: 40px;
}

/* CARD */

.card {
  width: 310px;
  overflow: hidden;
  border-radius: 2%;
  box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.2);
  margin-bottom: 30px;
  margin-right: 20px;
  cursor: pointer;
}

.card img {
  width: 100%;
  height: 200px;
  margin: 0;
}

.card .card-text h2 {
  font-weight: bold;
  display: flex;
  /* flex-direction: column;
  justify-content: center;
  align-items: center; */
}
</style>
