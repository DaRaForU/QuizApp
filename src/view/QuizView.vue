<script setup>
  import Question from '../components/Question.vue';
  import QuizHeader from '../components/QuizHeader.vue';
  import {useRoute} from 'vue-router';
  import quizes from '../data/quizes.json';
  import {ref, watch, computed} from 'vue';
  import Result from '../components/Result.vue';

  const route = useRoute();
  const quizId = parseInt(route.params.id);
  const currentQestionIndex = ref(0); 
  const quiz = quizes.find(q => q.id === quizId);
  const numberOfCorrectAnswer = ref(0);
  const showResults = ref(false);

  // const questionStatus = ref(`${currentQestionIndex.value}/${quiz.questions.length}`);
  // watch(() => currentQestionIndex.value, () => {
  //   questionStatus.value = `${currentQestionIndex.value}/${quiz.questions.length}`;
  // });

  const questionStatus = computed(() => {
    return `${currentQestionIndex.value}/${quiz.questions.length}`;
  });
  const barPercentage = computed(() => `${currentQestionIndex.value/quiz.questions.length*100}%`);

  const onOptionSelected = (isCorrect) => {
    // console.log('value: ' + isCorrect);

    if(isCorrect){
      numberOfCorrectAnswer.value += 1;
    }

    if(quiz.questions.length - 1 === currentQestionIndex.value){
      showResults.value = true;
    }

    currentQestionIndex.value += 1;

  };

</script>

<template>

  <div class="container-quiz">
    <QuizHeader 
      :questionStatus="questionStatus"
      :barPercentage="barPercentage"
    />

    <div>
      <Question
        v-if="!showResults"
        :question="quiz.questions[currentQestionIndex]" 
        @selectOption="onOptionSelected"
      />
      <Result
        v-else
        :quizQuestionLength="quiz.questions.length"
        :numberOfCorrectAnswer="numberOfCorrectAnswer"
      />
    </div>


    <!-- <button @click="currentQestionIndex += 1">Next Question</button> -->
  </div>
</template>

<style scoped>
  .container-quiz{
    max-width: 1000px;
    margin: 0 auto;
  }


</style>