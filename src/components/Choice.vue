<script setup>
    defineProps(['choice'])
</script>

<template>
    <div class="circle">
        <img :src="choice" alt="">
    </div>
</template>

<style scoped>
    .circle{
        width: 120px;
        height: 120px;
        margin: 25px 25px;
        display: flex;
        justify-content: center;
        align-items: center;
        border-radius: 50%;
        background-color: rgb(235, 235, 235);
        cursor: pointer;
        transition: .3s;
        box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
    }
    .circle:hover{
        scale: 1.3;
    }
</style>