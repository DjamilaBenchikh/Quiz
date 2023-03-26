<script setup>
 import Question from "../components/Question.vue"
 import QuizHeader from "../components/Header.vue" 
 import { useRoute} from "vue-router";
 import {ref,watch,computed} from "vue";
 import quizes from "../data/quizes.json";
 import Result from "../components/Result.vue"

 const route= useRoute();

 const quizId=parseInt(route.params.id);

 const quiz=quizes.find(q=> q.id === quizId);

 const currentQuestionIndex = ref(0);
 const numberOfCorrectAnswers =ref(0)

 //const questionStatus =ref(`${currentQuestionIndex.value}/${quiz.questions.length}`)

 watch(()=> currentQuestionIndex.value,() =>{
    questionStatus.value=`${currentQuestionIndex.value}/${quiz.questions.length}`
 })
 const questionStatus= computed(()=>
     `${currentQuestionIndex.value}/${quiz.questions.length}`
 )
 const barPercentage= computed(()=>`${currentQuestionIndex.value/quiz.questions.length *100}%`)
 
 const onOptionSelected = (isCorrect) =>
 {
     if(isCorrect){
        numberOfCorrectAnswers.value++;
     }
     currentQuestionIndex.value++
 }

</script>
<template>
    <div>
       
        <QuizHeader
        :questionStatus="questionStatus"
        :barPercentage="barPercentage"

        />
        <div>
            <Question
             v-if="truenpm"
             :question="quiz.questions[currentQuestionIndex]"
             @selectOption="onOptionSelected"
            />
            <Result 
            :numberOfCorrectAnswers="numberOfCorrectAnswers"
            />
        </div>
        <!--button @click="currentQuestionIndex++"> 
         Next Question</button-->
    </div>
</template>

<style scoped>
</style>