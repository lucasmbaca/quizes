<template>
    <div>
        <QuizHeader 
            :questionStatus="questionStatus" 
            :percentageBar="percentageBar"
        />
        <div>
            <Question 
                v-if="!ShowResults"
                :question="quiz.questions[currentQuestionIndex]" 
                @selectOption="onOptionSelected"
            />
            <Result 
                v-else
                :quizQuestionLength = "quiz.questions.length"
                :numberOfCorrectAnswer = "numberOfCorrectAnswer"
            />
        </div>
        
    </div>
</template>

<script setup>
import { ref, computed } from "vue";

import Question from "../components/Question.vue"
import QuizHeader from "../components/QuizHeader.vue"
import Result from "../components/Result.vue"

import {useRoute} from "vue-router"

import quizes from "../data/quizes.json"

const route = useRoute()
const quizId = parseInt(route.params.id);
const quiz = quizes.find(q => q.id === quizId)
const currentQuestionIndex = ref(0);
const numberOfCorrectAnswer = ref(0)
const ShowResults = ref(false);

const questionStatus = computed(() => `${currentQuestionIndex.value}/${quiz.questions.length}`)
const percentageBar = computed(() => `${currentQuestionIndex.value/quiz.questions.length * 100}%`)

const onOptionSelected = (isCorrect) => {
    if(isCorrect){
        numberOfCorrectAnswer.value++;
    }

    if(quiz.questions.length - 1 === currentQuestionIndex.value){
        ShowResults.value = true
    }
    currentQuestionIndex.value++
}
</script>

<style scoped>

</style>