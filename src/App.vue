<template>
  <div id="app">
    <h1>Would you rather?</h1>

    <would-you-rather 
    v-for="question in questions"
    v-bind:id="question.id"
    v-bind:question="question.wyrQuestion"
    v-bind:answer1="question.wyrAnswer1"
    v-bind:answer2="question.wyrAnswer2"
    v-on:answer-changed="answerChanged"></would-you-rather> <!--Running the component for WouldYouRather-->
    <!--v-on: taking the message and data from child when event established in child occurs-->
    <!--Created method answerChanged but will need to actually build out method below-->

    <!-- Commenting this out to instead create a component that houses the user's list answers
    <p>{{ userSelectionMessage }}</p> Creating a place to display user answer to user
        -->

    <h3>You would rather...</h3>
    <!--I can't the v-for to work here but if i just bind and run the for in the UserAnswers component it works but if questions are answered out of order it'll show a blank li-->
    <user-answers
      v-bind:answer="userSelectionMessage"
    ></user-answers>

  </div>
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'
import UserAnswers from './components/UserAnswers.vue'


export default {
  name: 'App',
  components: {
    WouldYouRather,
    UserAnswers
  },
  data() {
    return {
      questions: [
        {
          id: 0,
          wyrQuestion: 'Would you rather eat too much salt or too much sugar?',
          wyrAnswer1: 'Eat too much salt',
          wyrAnswer2: 'Eat too much sugar',
          // userSelectionMessage: ''
          //this is just the data, it's not showing to user yet
          //App will send this data to WouldYouRather in a prop value
        },
        {
          id: 1,
          wyrQuestion: 'Would you rather solve the socio-political issues in Yemen or North Korea?',
          wyrAnswer1: "Solve Yemen's problems",
          wyrAnswer2: "Solve North Korea's problems",
          // userSelectionMessage: ''
          //this is just the data, it's not showing to user yet
          //App will send this data to WouldYouRather in a prop value
        },
        {
          id: 2,
          wyrQuestion: 'Would you rather be a professional lolligagger or a professional goofball',
          wyrAnswer1: 'Be a Lolligagger',
          wyrAnswer2: 'Be a Goofball',
          // userSelectionMessage: ''
          //this is just the data, it's not showing to user yet
          //App will send this data to WouldYouRather in a prop value
        }
      ],
      userSelectionMessage: []
    }
  },
  methods: {
    answerChanged(choice, id) { //choice is the argument data being sent from the child
      // added id to identify which answer has changed and assigning the corresponding choice to that id even if it changes
      this.userSelectionMessage[id] = choice
      

      // TRIED THIS FROM THE STUDENT SIGN IN IN ATTEMPT TO HIDE BLANK BULLET POINTS
      // let updateAnswer = this.userSelectionMessage.find (function(s) {
      //   if (s.id === userSelectionMessage.id) {
      //     //find method will search an array for the first matching value
      //     //so above we;re searching the student array for the exact name and starID match
      //     // and if found we're returning true to update the present/absent status
      //     return true
      //   }
      // })

      // if (updateAnswer) {
      //   updateAnswer.choice = choice
      //   this.userSelectionMessage[id] = updateAnswer
      // }  
    }
  }
}

</script>

<style>

body {
  background: darkkhaki;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background: sandybrown;
}
</style>
