<script setup>
    defineProps(['result'])
</script>

<template>
    <div class="result">
        <h1 class="result">{{result}}</h1>
    </div>
</template>

<style scoped>
   .result{
        font-size: 30px;
        font-weight: 700;
   }
</style>