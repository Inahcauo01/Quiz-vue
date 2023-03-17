<template>
    <div class="question">
      <h2>Question {{index + 1}}:</h2>
      <p>{{question.text}}</p>
      <ul>
        <li v-for="(answer, index) in question.answers" :key="index">
          <label>
            <input type="radio" :value="answer" v-model="selectedAnswer">{{answer}}
          </label>
        </li>
      </ul>
      <button @click="submitAnswer">Next</button>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      question: {
        type: Object,
        required: true,
      },
      index: {
        type: Number,
        required: true,
      },
    },
    data() {
      return {
        selectedAnswer: '',
      };
    },
    methods: {
      submitAnswer() {
        this.$emit('answer-selected', this.selectedAnswer);
        this.selectedAnswer = '';
      },
    },
  };
  </script>
  
  <style scoped>
  .question {
    max-width: 500px;
    margin: 0 auto;
    text-align: center;
  }
  </style>