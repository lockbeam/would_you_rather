<template>
  <div id="app">
    <h1>Would you rather?</h1>

    <would-you-rather v-bind:question="wyrQuestion"
    v-bind:answer1="wyrAnswer1"
    v-bind:answer2="wyrAnswer2"
    v-on:answer-changed="answerChanged"></would-you-rather> <!--Running the component for WouldYouRather-->
    <!--v-on: taking the message and data from child when event established in child occurs-->
    <!--Created method answerChanged but will need to actually build out method below-->

    <p>{{ userSelectionMessage }}</p> <!--Creating a place to display user answer to user-->

  </div>
</template>

<script>
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  data() {
    return {
      wyrQuestion: 'Would you rather eat too much salt or too much sugar?',
      wyrAnswer1: 'Too much salt',
      wyrAnswer2: 'Too much sugar',
      userSelectionMessage: ''
      //this is just the data, it's not showing to user yet
      //App will send this data to WouldYouRather in a prop value
    }
  },
  methods: {
    answerChanged(choice) { //choice is the argument data being sent from the child
      this.userSelectionMessage = `Thanks! You chose: ${choice}.` 
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
