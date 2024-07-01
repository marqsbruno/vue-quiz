<script setup>
import QuestionCard from '../components/QuestionCard.vue'
import QuizHeader from '@/components/QuizHeader.vue'
import ResultFinal from '@/components/ResultFinal.vue'
import q from '../data/quizzes.json'

import { useRoute } from 'vue-router'
import { ref, computed } from 'vue'

const { params } = useRoute()
const quizID = parseInt(params.id)

const quiz = q.find((e) => e.id === quizID)

const currentQuestionIndex = ref(0)
const correctPoints = ref(0)
const showResult = ref(false)

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

const onSelectOption = (isCorrect) => {
  if (isCorrect) {
    correctPoints.value++
  }

  if (quiz.questions.length - 1 === currentQuestionIndex.value) {
    showResult.value = true
  }

  currentQuestionIndex.value++
}
</script>
<template>
  <div>
    <QuizHeader :questionBar="questionBar" :barPercentage="barPercentage" />
    <div>
      <QuestionCard
        v-if="!showResult"
        :question="quiz.questions[currentQuestionIndex]"
        @selectOption="onSelectOption"
      />
      <ResultFinal :correctAnswers="correctPoints" :quizLength="quiz.questions.length" v-else />
    </div>
    <!-- <button v-on:click="currentQuestionIndex++">aaaaaa</button> -->
  </div>
</template>
