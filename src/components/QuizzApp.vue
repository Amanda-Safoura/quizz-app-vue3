<template>
  <div class="container mt-5 p-5" style="max-width: 750px; background-color: #fcfcfcff">
    <p class="text-center fs-4 mb-4">{{ datas.title }}</p>

    <div v-if="questionId + 1 <= datas.questions.length">
      <div v-if="datas.questions[questionId]">
        <QuizzQuestion
          :key="questionId"
          v-model:score="score"
          v-model:question-id="questionId"
          v-model:progress-value="progressValue"
          :nb_questions="datas.questions.length"
          :question="datas.questions[questionId].question"
          :choices="datas.questions[questionId].choices"
          :correct_answer="datas.questions[questionId].correct_answer"
        ></QuizzQuestion>
      </div>
    </div>
    <div v-else>
      <div class="row-cols-7">
        <div v-if="score >= datas.minimum_score">
          <div class="h3 mb-5">Bravo !</div>
          <p class="h4">Votre score est de {{ score + '/' + datas.questions.length }}</p>
          <p class="h5">{{ datas.success_message }}</p>
        </div>
        <div v-else>
          <div class="h3 mb-5">Désolé :(</div>
          <p class="h4">Votre score est de {{ score + '/' + datas.questions.length }}</p>
          <p class="h5">{{ datas.failure_message }}</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>
import { onMounted, ref } from 'vue'
import QuizzQuestion from './QuizzQuestion.vue'

const questionId = ref(0)
const datas = ref({
  questions: []
})
const score = ref(0)
const progressValue = ref(null)

onMounted(() => {
  fetch('http://localhost:5173/quizz.json')
    .then((res) =>
      res.json().then((json) => {
        datas.value = json
        progressValue.value = Math.ceil((1 / datas.value.questions.length) * 100)
      })
    )
    .catch((err) => console.error('An error occured : ' + err))
})
</script>
