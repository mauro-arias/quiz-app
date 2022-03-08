<template>
    <div class='card p-5 mt-5 mx-5 flex justify-start flex-wrap flex-col w-5/6'>
        <div v-if='this.questionNumber !== this.category.questions.length'>
            <p class='text-right text-custom-blue'><i class="ai-hashtag mr-1"></i>{{`${this.questionNumber+1}/${this.category.questions.length}`}}</p>
            <h1 class='text-2xl text-left text-custom-dark'>{{this.category.questions[this.questionNumber].question}}</h1>
            <ul class='flex flex-col mt-5'>
                <li 
                    @click="select(index)" 
                    v-for="(option, index) in this.category.questions[this.questionNumber].options" :key="index" 
                    :class='[this.optionSelected == index ? "bg-custom-blue text-white" : "bg-custom-gray","option"]'
                    >{{option}}</li>
            </ul>
            <div class='flex justify-center items-center mt-7'>
                <Button 
                    @click="nextQuestion" 
                    :class="[this.optionSelected !== null ? 'primary-btn' : 'disabled']" icon='ai-circle-chevron-right-fill' 
                    text='Siguiente'/>
            </div>
        </div>
        <div v-else>
            <h1 class='text-2xl text-center text-custom-dark'>¡Finalizó las preguntas!</h1>
            <p class='mt-5 text-lg'>Usted ha contestado correctamente:</p>
            <div class='flex justify-center items-center flex-col'>
                <p class='text-5xl mt-2 text-green-500 p-8 border-2 border-green-500 rounded-full'>{{this.answeredCorrectly}}/{{this.category.questions.length}}</p>
                <p class='mt-1 text-lg'>preguntas!</p>
            </div>
            <div class='flex justify-center items-center mt-7 flex-col gap-y-2'>
                <Button 
                        @click="toggleResults" 
                        :class="[true ? 'primary-btn' : 'disabled', 'w-64', 'justify-center']" :icon='this.showResults ? "ai-cross" : "ai-statistic-up"' 
                        :text='this.showResults ? "Ocultar resultados" : "Mostrar resultados"'/>
                
                <Results v-if="this.showResults" :category='this.category' :answers="this.answers"/>
                <Button 
                        @click="done" 
                        :class="[true ? 'primary-btn' : 'disabled', 'w-64', 'justify-center']" icon='ai-door' 
                        text='Volver al inicio'/>
            </div>
        </div>
    </div>
</template>

<script>
import Button from './Button.vue'
import Results from './Results.vue'
import quizData from '../quizData.json'

export default {
    name: 'Question',
    components: {
        Button,
        Results
    },
    data(){
        return {
            category: null,
            questionNumber: 0,
            optionSelected: null,
            answeredCorrectly: 0,
            answers: [],
            showResults: false
        }
    },
    created(){
        this.category = quizData.find(e=>e.category === this.$store.state.category)
    },
    methods: {
        select(index){
            this.optionSelected = index
        },
        nextQuestion(){
            if(this.optionSelected !== null){ // Checkear si el usuario seleccionó su respuesta
                // Guardar su respuesta
                this.answers.push(this.optionSelected)
                
                if(this.optionSelected === this.category.questions[this.questionNumber].correct){
                    this.answeredCorrectly++
                }
                this.questionNumber++
                this.optionSelected = null
            }
            if(this.questionNumber === this.category.questions.length){
            }
            // else if ,Quizas añadir aca la condicion para saber si terminó con las preguntas

        },
        toggleResults(){
            this.showResults = !this.showResults
        },
        done(){
            this.$router.push('/')
        }
    }
}
</script>