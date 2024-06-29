<script setup>
import QuestionCard from '../components/QuestionCard.vue'
import QuizHeader from '@/components/QuizHeader.vue'
import q from '../data/quizzes.json'

import { useRoute } from 'vue-router'
import { ref, computed } from 'vue'

const { params } = useRoute()
const quizID = parseInt(params.id)

const quiz = q.find((e) => e.id === quizID)

const currentQuestionIndex = ref(0)

/* const questionBar = ref(`${currentQuestionIndex.value}/${quiz.questions.length}`)
watch(
  () => currentQuestionIndex.value,
  () => {
    questionBar.value = `${currentQuestionIndex.value}/${quiz.questions.length}`
  }
) */

const questionBar = computed(() => {
  return `${currentQuestionIndex.value}/${quiz.questions.length}`
})

const barPercentage = computed(
  () => `${(currentQuestionIndex.value / quiz.questions.length) * 100}%`
)
</script>
<template>
  <div>
    <QuizHeader :questionBar="questionBar" :barPercentage="barPercentage" />
    <div>
      <QuestionCard :question="quiz.questions[currentQuestionIndex]" />
    </div>
  </div>
</template>
