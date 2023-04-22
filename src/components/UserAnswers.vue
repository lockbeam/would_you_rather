<template>


<ul>
    <li
        v-for="answer in answer">
            {{ answer }}    
    </li>
</ul>
</template>

<script>

export default {
  name: 'UserAnswers',
  props: {
    answer: Array
  }
}

</script>

<style scoped>

h3 {
    font-size: 25px
}

li {
 list-style-type:square;
 list-style-position:inside;
}

.styles{
display: none;
}

</style>