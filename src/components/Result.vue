<template>
    <div class="results">
        <p>Your Result</p>
        <h1>{{numberOfCorrectAnswer}}/{{quizQuestionLength}}</h1>

        <RouterLink to="/">go back</RouterLink>
    </div>
       
</template>

<script setup >
    import { defineProps } from 'vue'; 

    import {RouterLink} from "vue-router"

    const {quizQuestionLength, numberOfCorrectAnswer} = defineProps(["quizQuestionLength","numberOfCorrectAnswer"])
</script>

<style scoped>
.results{
    text-align: center;
    padding: 100px 0;
}

p{
    font-size: 25px;
}

h1{
    font-size: 30px;
}
</style>