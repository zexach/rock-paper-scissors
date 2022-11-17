<script setup>
    import Choice from './Choice.vue';

    defineProps(['opponentPick'])

</script>

<template>
    <div class="opponent-pick">
        <h3>OPPONENT'S PICK</h3>
        <Choice choice="https://i.imgur.com/B9bhcFt.png" style="border: 15px solid #2ce014" v-if="opponentPick === 'paper'" />
        <Choice choice="https://i.imgur.com/o41ORt9.png" style="border: 15px solid #ffd70d" v-if="opponentPick === 'rock'" />
        <Choice choice="https://i.imgur.com/hYMBReL.png" style="border: 15px solid red" v-if="opponentPick === 'scissors'" />
    </div>
</template>

<style scoped>
    h3{
        font-weight: 700;
    }
    .opponent-pick{
        display: flex;
        flex-direction: column-reverse;
        align-items: center;
    }
</style>