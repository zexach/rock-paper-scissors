<script setup>
    import Choice from './Choice.vue';

    defineProps(['opponentPick'])

</script>

<template>
    <div class="opponent-pick">
        <h3>OPPONENT'S PICK</h3>
        <Choice choice="/src/img/icon-paper.svg" style="border: 15px solid #2ce014" v-if="opponentPick === 'paper'" />
        <Choice choice="/src/img/icon-rock.svg" style="border: 15px solid #ffd70d" v-if="opponentPick === 'rock'" />
        <Choice choice="/src/img/icon-scissors.svg" style="border: 15px solid red" v-if="opponentPick === 'scissors'" />
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