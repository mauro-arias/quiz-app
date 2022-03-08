<template>
  <div class="container mx-auto mt-5">
      <h1 class='text-custom-dark text-xl'>Tema: {{$store.state.category}}</h1>
      <Question v-if="this.$store.state.category !== ''" />
  </div>
</template>

<script>

import Question from '../components/Question.vue'

export default {
  name: 'Quiz',
  components: {
    Question
  },
  created(){
    if(this.$store.state.category === ''){
      this.$router.push('/')
    }
  }
}
</script>