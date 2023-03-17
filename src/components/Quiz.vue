<template>
    <div class="quiz">
      <h1 v-if="currentState === 'intro'">Welcome to the Quiz App!</h1>
      <div v-if="currentState === 'intro'">
        <label for="name">Enter your name:</label>
        <input type="text" id="name" v-model="name">
        <button @click="startQuiz">Next</button>
      </div>
      <Question v-if="currentState === 'quiz'" :question="questions[currentQuestionIndex]" @answer-selected="checkAnswer" />
      <Result v-if="currentState === 'result'" :name="name" :score="score" :totalQuestions="questions.length" />
    </div>
  </template>
  
  <script>
  import Question from './Question.vue';
  import Result from './Result.vue';
  
  export default {
    components: {
      Question,
      Result,
    },
    data() {
      return {
        name: '',
        currentState: 'intro',
        currentQuestionIndex: 0,
        selectedAnswer: '',
        score: 0,
        questions: [
          {
            text: 'Why is AWS more economical than traditional data centers for applications with varying compute workloads?',
            answers: ['f Amazon EC2 costs are billed on a monthly basis',
                    'f Users retain full administrative access to their Amazon EC2 instances.',
                    'Amazon EC2 instances can be launched on demand when needed',
                    'f Users can permanently run enough instances to handle peak workloads'],
            correctAnswer: 'Amazon EC2 instances can be launched on demand when needed',
          },
          {
            text: 'Which AWS service would simplify the migration of a database to AWS?',
            answers: ['f AWS Storage Gateway',
            'AWS Database Migration Service (AWS DMS)',
            'f Amazon EC2',
            'f Amazon AppStream 2.0'],
            correctAnswer: 'AWS Database Migration Service (AWS DMS)',
          },
          {
            text: 'Which AWS offering enables users to find, buy, and immediately start using software solutions in their AWS environment?',
            answers: ['f AWS Config',
            'f AWS OpsWorks',
            'f AWS SDK',
            'AWS Marketplace'],
            correctAnswer: 'AWS Marketplace',
          },
          {
            text: 'Which AWS networking service enables a company to create a virtual network within AWS?',
            answers: ['f AWS Config',
            'f Amazon Route 53',
            'f AWS Direct Connect',
            'Amazon Virtual Private Cloud (Amazon VPC)'],
            correctAnswer: 'Amazon Virtual Private Cloud (Amazon VPC)',
          },
          {
            text: 'Which of the following is an AWS responsibility under the AWS shared responsibility model?',
            answers: ['f Configuring third-party applications',
            'Maintaining physical hardware',
            'f Securing application access and data',
            'f Managing guest operating systems'],
            correctAnswer: 'Maintaining physical hardware',
          },
          {
            text: 'Which component of the AWS global infrastructure does Amazon CloudFront use to ensure low-latency delivery?',
            answers: ['f AWS Regions',
            'Edge locations',
            'f Availability Zones',
            'f Virtual Private Cloud (VPC)'],
            correctAnswer: 'Edge locations',
          },
          
          {
            text: 'How would a system administrator add an additional layer of login security to a user\'s AWS Management Console?',
            answers: ['f Use Amazon Cloud Directory',
            'f Audit AWS Identity and Access Management (IAM) roles',
            'Enable multi-factor authentication',
            'f Enable AWS CloudTrail'],
            correctAnswer: 'Enable multi-factor authentication',
          },
          {
            text: "Which service can identify the user that made the API call when an Amazon EC2 instance is terminated?",
            answers:['f AWS Trusted Advisor',
            'AWS CloudTrail',
            'f AWS X-Ray',
            'f AWS Identity and Access Management (AWS IAM)'],
            correctAnswer: "AWS CloudTrail",
          },
          {
            text: "Which service would be used to send alerts based on Amazon CloudWatch alarms?",
            answers:['Amazon Simple Notification Service (Amazon SNS)',
            'f AWS CloudTrail',
            'f AWS Trusted Advisor',
            'f Amazon Route 53'],
            correctAnswer: "Amazon Simple Notification Service (Amazon SNS)",
          },
          {
            text: "Where can a user find information about prohibited actions on the AWS infrastructure?",
            answers:['f AWS Trusted Advisor',
            'f AWS Identity and Access Management (IAM)',
            'f AWS Billing Console',
            'AWS Acceptable Use Policy'],
            correctAnswer: "AWS Acceptable Use Policy",
          },
        ],
      };
    },
    methods: {
      startQuiz() {
        this.currentState = 'quiz';
      },
      checkAnswer(answer) {
        if (answer === this.questions[this.currentQuestionIndex].correctAnswer) {
          this.score++;
        }
  
        if (this.currentQuestionIndex === this.questions.length - 1) {
          this.currentState = 'result';
        } else {
          this.currentQuestionIndex++;
        }
      },
    },
  };
  </script>
  
  <style scoped>
  </style>