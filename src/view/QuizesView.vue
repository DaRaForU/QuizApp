<script setup>
  import Card from '../components/Card.vue';
  import q from '../data/quizes.json';
  import {ref} from 'vue';

  const quizes = ref(q);
</script>

<template>
  <div class="container">
    <header>
      <h1>Quizes</h1>
      <input type="text" placeholder="Search...">
    </header>

    <div class="options-container">

      <Card v-for="quiz in quizes" :key="quiz.id" :quiz="quiz" />

    </div>
  </div>
</template>

<style scoped>
  .container{
    max-width: 1000px;
    margin: 0 auto;
  }
  header{
    margin-bottom: 10px;
    margin-top: 30px;
    display: flex;
    align-items: center;
  }
  header h1{
    font-weight: bold;
  }
  header input{
    border: none;
    padding: 10px;
    border-radius: 5px;
    margin-left: 10px;
  }

  .options-container{
    display: flex;
    flex-wrap: wrap;
  }
  
</style>
