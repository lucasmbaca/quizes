<script setup>
    import { defineProps } from 'vue';
    import { useRouter } from 'vue-router';

    const router = useRouter()
    const {quiz} = defineProps(['quiz'])
    
    const navToQuiz = () => {
      router.push(`/quiz/${quiz.id}`)
    }
</script>

<template>
    <div class="card" @click="navToQuiz">
        <img :src="quiz.img" alt="imagen de la carta">
        <div class="card-text">
            <h2>{{quiz.name}}</h2>
            <p>{{quiz.questions.length}}</p>
        </div>
    </div>
</template>

<style scoped>
  /* CARD */
  .card{
    width: 310px;
    overflow: hidden;
    border-radius: 2%;
    box-shadow: 1px 1px 10px rgba(0, 0, 0, 0.1);
    margin-bottom: 35px;
    margin-right: 20px;
    cursor: pointer;
  }

  .card img{
    width: 100%;
    height: 190px;
    margin: 0%;
  }

  .card .card-text{
    padding: 0 5px;
  }

  .card .card-text{
    padding: 0 5px;
  }

  .card-text h2{
    font-weight: bold;
  }

</style>