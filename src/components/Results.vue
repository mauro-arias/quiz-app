<template>
    <div class="card w-full p-5 flex flex-col text-left">
        <p class='text-custom-red'>Resultados</p>
        <ul class='mt-4'>
            <!-- <li class='text-custom-blue'><i class='ai-check'></i> Incorrecto</li>
            <li class='text-custom-red'><i class='ai-cross'></i> Correcto</li> -->
            <div v-for="(question, index) in this.category.questions" :key="index"  class='flex flex-col'>
                <li :class='[question.correct === answers[index] ? "text-custom-blue" : "text-custom-red","my-2"]'><i :class='[question.correct === answers[index] ? "ai-check" : "ai-cross", "mr-1"]'></i>{{question.question}}</li>
                <div>
                    <p class='text-gray-500 ml-5 text-sm'>Opción correcta: {{question.options[question.correct]}}</p>
                    <p class='text-gray-500 ml-5 text-sm'>Seleccionaste: {{question.options[answers[index]]}}</p>
                </div>
            </div>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'Results',
    props: {
        category: Object,
        answers: Array
    }
}
</script>