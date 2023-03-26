<script setup>
  import {defineProps} from "vue";
  import {useRouter} from "vue-router"
  
  const router=useRouter();
  const props= defineProps(['quiz']);
  const navigateToQuiz=(v)=>{
   router.push(`/quiz/${v}`)
 }
</script>


<template>
 
  <div @click="navigateToQuiz(quiz.id)" class="card">
  <img :src="quiz.img" alt="" >
  <div class="card-text">
    <h2> {{quiz.name}}</h2>
    <p> {{ quiz.questions.length }} questions</p>
  </div>
</div>
</template>

<style scoped>
.card{
    width: 310px;
    overflow: hidden;
    border-radius: 2%;
    box-shadow: 5px 5px 10px rgba(168, 115, 115, 0.1);
    margin-bottom: 35px;
    margin-right: 20px;
    cursor: pointer;
  }
  .card img{
    width:100%;
    height: 190px;
    margin: 0;
  }
  .card .card-text{
    padding: 0 5px
  }
  .card h2{
      
  }
</style>