<script setup>
import MainCards from '../components/MainCards.vue'
import { ref, watch } from 'vue'
import q from '../data/quizzes.json'

const quizzes = ref(q)
const searchText = ref('')

watch(searchText, () => {
  quizzes.value = q.filter((e) => e.name.toLowerCase().includes(searchText.value.toLowerCase()))
  console.log(quizzes.value)
})
</script>

<template>
  <div>
    <header>
      <h1>Quizzes</h1>
      <input type="text" placeholder="Search..." v-model.trim="searchText" />
    </header>
    <div class="options-container">
      <MainCards v-for="quiz in quizzes" :key="quiz.id" :quizProp="quiz" />
      <!-- <div v-for="quiz in quizzes" :key="quiz.id" class="card">
        <img v-bind:src="quiz.img" alt="" />
        <div class="card-text">
          <h2>{{ quiz.name }}</h2>
          <p>{{ quiz.questions.length }} questions</p>
        </div>
      </div> -->
    </div>
  </div>
</template>

<style scoped>
header {
  /* border: 1px solid black; */
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
</style>
