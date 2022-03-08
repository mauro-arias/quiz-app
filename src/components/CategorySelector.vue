<template>
  <div class="container mx-auto mt-5">
    <h1 class='text-custom-dark text-xl'>¡Bienvenido! Seleccione un tema: </h1>
    <Category name='Programación' img='programacion.svg' :isSelected='this.$store.state.category === "Programación" ? true : false'/>
    <Category name='Deporte' img='deporte.svg' :isSelected='this.$store.state.category === "Deporte" ? true : false'/>
    <div class='flex justify-center items-center mt-7'>
      <Button :class="[this.$store.state.category !== '' ? 'primary-btn' : 'disabled']" @click='startQuiz' icon='ai-check' text='Seleccionar'/>
    </div>
  </div>
</template>

<script>
import Category from './Category.vue'
import Button from './Button.vue'

export default {
  name: 'CategorySelector',
  components: {
    Category,
    Button
  },
  methods: {
    startQuiz(){
      if(this.$store.state.category !== ''){
        this.$router.push('/quiz')
      }
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
