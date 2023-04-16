<template>
  <div class="wyr">
   
    <h2>Please make your choice</h2>

    <h3>{{ question }}</h3> <!--Recieving from v-bind in App - THIS ACTUALLY DISPLAYS THE QUESITON-->

    <!--Creating radio buttons displaying data from App for answers to questions-->
    <input type="radio" v-model="choice" v-bind:value="answer1" v-on:change="choiceMade"> <!--v-bind: when this button is selected the value for answer1 is stored in the data as the choice-->
    <label>{{ answer1 }}</label>

    <input type="radio" v-model="choice" v-bind:value="answer2" v-on:change="choiceMade"> <!--v-on: using this to store an event and then send a message to parent App that a choice has been made to update final display message to user-->
    <label>{{ answer2 }}</label>


  </div>
</template>

<script>
export default {
  name: 'WouldYouRather',
  //HERE'S WHERE WOULD YOU RATHER IS RECEIVING INFO FROM APP
  props: {
    question: String,
    //use the type - in this case String
    answer1: String,
    answer2: String,
  },
  data() {
    return {
      choice: ''
      //this is important because it's storing the choice for whichever WYR question is being displayed at the time - otherwise the answer would affect previous WYR decisions as well
    }
  },
  methods: {
    choiceMade() {
      this.$emit('answer-changed', this.choice)
      //Dollar emit is a vue method used to send a message to parent
      //Best practice to use a - somewhere in the name
      //this.choice is sending the data
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}

.wyr {
  border: 2px blue solid;
  background: lemonchiffon;
}


</style>
