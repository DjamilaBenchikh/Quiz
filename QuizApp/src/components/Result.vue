<script setup>

import {defineProps} from "vue";

const props=defineProps(["numberOfCorrectAnswers"])
</script>


<template>
    <div class="results">
        <p> Your Results ...</p>
        <h1>
            {{numberOfCorrectAnswers}}/3
        </h1>
    </div>
</template>

<style scoped>
 .results{
    text-align:center;
    padding: 30px 0;
 }
 p{
  font-size:25px ;
 }
 h1{
    font-size: 25px;
 }
</style>