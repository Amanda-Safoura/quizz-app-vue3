<template>
  <ProgressBar
    class="mb-5"
    label="quizz_progress"
    height="10px"
    :progressValue="progressValue"
  ></ProgressBar>

  <div class="row-cols-7">
    <form @submit.prevent="saveAnswer" :id="`question-${questionId}`">
      <p class="h5 mb-3 text-center">{{ question }}</p>
      <div v-for="(choice, index) in choices" :key="index" class="mb-3">
        <ul>
          <li :id="`choice-${questionId}_${index}`">
            <RadioButton
              :radio-label="choice"
              :value="choice"
              v-model="answer"
              :id="`question_${questionId}-${index}`"
              :name="`question_${questionId}`"
              @check="updateAnswer"
            ></RadioButton>
          </li>
        </ul>
      </div>
      <div class="mb-3 text-end">
        <SimpleButton
          type="submit"
          :disabled="!hasAnswered"
          class="btn-primary btn-lg"
          :id="`submitButton_${questionId}`"
          >Question Suivante</SimpleButton
        >
      </div>
    </form>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import RadioButton from './RadioButton.vue'
import SimpleButton from './SimpleButton.vue'
import ProgressBar from './ProgressBar.vue'

const score = defineModel('score')
const questionId = defineModel('questionId')
const progressValue = defineModel('progressValue')

const answer = ref(null)
const hasAnswered = ref(false)

const props = defineProps({
  question: String,
  choices: Array,
  correct_answer: String,
  nb_questions: Number
})

const updateAnswer = (choice) => {
  answer.value = choice
  hasAnswered.value = answer.value !== null
}

const saveAnswer = () => {
  questionId.value++
  progressValue.value = Math.ceil((questionId.value / props.nb_questions) * 100)

  if (answer.value == props.correct_answer) score.value++
}
</script>

<style scoped>
ul {
  list-style: none;
}
</style>
