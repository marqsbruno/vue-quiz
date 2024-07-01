<script setup>
import { defineProps } from 'vue'
import { useRouter } from 'vue-router'

const { quizProp } = defineProps(['quizProp'])

const router = useRouter()

const navigateToQuiz = () => {
  router.push(`/quiz/${quizProp.id}`)
}
</script>

<template>
  <div class="card" @click="navigateToQuiz">
    <img :src="quizProp.img" alt="" />
    <div class="card-text">
      <h2>{{ quizProp.name }}</h2>
      <p>{{ quizProp.questions.length }} questions</p>
    </div>
  </div>
</template>

<style scoped>
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
