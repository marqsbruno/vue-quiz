<script setup>
import QuestionCard from '../components/QuestionCard.vue'
import QuizHeader from '@/components/QuizHeader.vue'
import q from '../data/quizzes.json'

import { useRoute } from 'vue-router'
import { ref } from 'vue'

const { params } = useRoute()
const quizID = parseInt(params.id)

const quiz = q.find((e) => e.id === quizID)

const currentQuestionIndex = ref(0)
</script>
<template>
  <div>
    <QuizHeader />
    <div>
      <QuestionCard :question="quiz.questions[currentQuestionIndex]" />
    </div>
  </div>
</template>
