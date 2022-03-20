<script setup>
import { ref, computed } from "vue";
const questions = ref([
  {
    question: "What is Vue Js?",
    answer: 0,
    option: [
      "A front end framework",
      "A library",
      "A state management library",
    ],
    selected: null,
  },
  {
    question: "What is Vuex?",
    answer: 0,
    option: [
      "A library for vueing x",
      "A markup language",
      "A state management library",
    ],
    selected: null,
  },
  {
    question: "What is Vue Router used for?",
    answer: 0,
    option: [
      "A library for vueing x",
      "A markup language",
      "A state management library",
      "Quizzes",
    ],
    selected: null,
  },
]);
const quizCompleted = ref(false);
const currentQuestion = ref(0);
const score = computed(() => {
  let value = 0;
  questions.value.map((q) => {
    if (q.selected == q.answer) {
      value++
    }
  })
  return value
});
const getCurrentQuestion = computed(() => {
  let question = questions.value[currentQuestion.value];
  question.index = currentQuestion.value;
  return question;
});
const setAnswer = (evt) => {
  questions.value[currentQuestion.value].selected = evt.target.value;
  evt.target.value = null;
};
const nextQuestion = () => {
  if (currentQuestion.value < questions.value.length - 1) {
    currentQuestion.value++;
  } else {
    quizCompleted.value = true;
  }
};
</script>

<template>
  <main class="app">
    <h1>The Quiz</h1>
    <section class="quiz">
      <div class="quiz-info">
        <span class="question">{{getCurrentQuestion.question}}</span>
      </div>
    </section>
  </main>
</template>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  font-family: "Montserra", sans-serif;
}
body {
  background-color: #271c36;
  color: #fff;
}
</style>
