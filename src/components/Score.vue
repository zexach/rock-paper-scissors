<script setup>
    defineProps(['score'])
</script>

<template>
    <div class="score-content">
        <p class="score-text">SCORE</p>
        <h2 class="score-value">{{score}}</h2>
    </div>
</template>

<style scoped>
    .score-content{
        padding: 5px 20px;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        border-radius: 5px;
        color: black;
        background-color: white;
    }
   .score-text{
    font-weight: 500;
   }
   .score-value{
    font-size: 30px;
    font-weight: 700;
   }
</style>