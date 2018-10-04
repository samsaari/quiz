<template>
  <div class="quiz">
    <h1>{{ questionIndex / quiz.questions.length * 100 }} %</h1>
  <div v-for="(question, index) in quiz.questions">
    <div v-show="index === questionIndex">
      <h2>{{ question.text }}</h2>
      <ol>
        <li v-for="response in question.responses">
          <label>
            <input type="radio" 
                   v-bind:value="response.correct" 
                   v-bind:name="index" 
                   v-model="userResponses[index]"> {{response.text}}
          </label>
        </li>
      </ol>
      <button v-if="questionIndex > 0" v-on:click="prev">
        prev
      </button>
      <button v-on:click="next">
        next
      </button>
    </div>
  </div>
  <div v-show="questionIndex === quiz.questions.length">
    <h2>
    Quiz finished
  </h2>
    <p>
      Total score: {{ score() }} / {{ quiz.questions.length }}
    </p>
  </div>
  </div>
</template>

<script>
const quiz = {
  title: 'My quiz',
  questions: [
    {
      text: "Question 1",
      responses: [
        {text: 'Wrong!'}, 
        {text: 'Right!', correct: true}, 
      ]
    }, {
      text: "Question 2",
      responses: [
        {text: 'Right!', correct: true}, 
        {text: 'Wrong!'}, 
      ]
    }, {
      text: "Question 3",
      responses: [
        {text: 'Right!', correct: true}, 
        {text: 'Wrong!'}, 
      ]
    }, {
      text: "Question 4",
      responses: [
        {text: 'Right!', correct: true}, 
        {text: 'Wrong!'}, 
      ]
    } 
  ]
};
export default {
  data() {
    return {
      quiz: quiz,
      // Store current question index
      questionIndex: 0,
      userResponses: Array(quiz.questions.length).fill(false)
    }
  },
  methods: {
    // Go to next question
    next() {
      this.questionIndex++;
    },
    // Go to previous question
    prev() {
      this.questionIndex--;
    },
    // Return "true" count in userResponses
    score() {
      return this.userResponses.filter((val) => { return val }).length;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
