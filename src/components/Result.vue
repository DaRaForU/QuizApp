<script setup>
  import { defineProps } from 'vue';
  import { RouterLink } from 'vue-router';

  const {quizQuestionLength, numberOfCorrectAnswer} = defineProps(['quizQuestionLength', 'numberOfCorrectAnswer']);


</script>

<template>

  <div class="results">
    <p>Your Results...</p>
    <h1>{{numberOfCorrectAnswer}}/{{quizQuestionLength}}</h1>

    <RouterLink to="/home" class="back-home">Back Home</RouterLink>
  </div>


</template>

<style scoped>
  .results{
    text-align: center;
    padding: 100px 0;
  }
  p{
    font-size: 25px;
  }
  h1{
    font-size: 80px;
  }

  .back-home{
     color: black;
     text-decoration: none;
     background-color: bisque;
     padding: 10px;
     border-radius: 4px;
  }

</style>