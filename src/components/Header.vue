<script setup>
    defineProps(['name'])
</script>

<template>
    <div class="header">
      <h2 class="game-name">{{name}}</h2>
    </div>
</template>

<style scoped>
   .game-name{
        font-size: 20px;
        font-weight: 600;
   }
</style>