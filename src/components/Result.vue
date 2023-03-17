<template>
    <div class="result">
      <h2>Results for {{name}}</h2>
      <p>You scored {{score}} out of {{totalQuestions}}!</p>
    </div>
  </template>
  
  <script>
  export default {
    props: {
      name: {
        type: String,
        required: true,
      },
      score: {
        type: Number,
        required: true,
      },
      totalQuestions: {
        type: Number,
        required: true,
      },
    },
  };
  </script>
  
  <style scoped>
  .result {
    max-width: 500px;
    margin: 0 auto;
    text-align: center;
  }
  </style>